# PasswordChecker

This repository contains code, and a PDF report, for a stand-alone password checker web application designed for use by children.

This application was created as part of an assessed exercise for the Human-Centred Security course at the University of Glasgow. Furthermore, I participated in this exercise as part of a 3-person team, please see the [report](Report.pdf) for further details on the team.

## Set-Up

The password checker is provided as an HTML page ([checker.html](checker.html)) with functionality implemented in a javascript file ([script.js](script.js)) and styles provided in a css file ([styles.css](styles.css)). 
Other resources (images) used for the interface are in the [res folder](res/). 
To use the application all a user needs to do is open the ‘checker.html’ file in any modern web browser, while making sure all files are grouped together in one folder.

## Report

Although there is a quick summary here in this README, a full report on the project can be found here: [REPORT](Report.pdf).

## Video

Alongside the report, our group also produced a video that explains the functionality of the password checker application, and the design decisions that guided us to create an application that achieves the desired security outcomes while best suiting the needs of the intended user demographic (children). The link to the video is here: [VIDEO](https://youtu.be/4ivnIqJ8BI8).

------------

We are all aware that children are using internet connected devices more frequently now than ever before, so it is becoming more important that considerations are made for them with regard to usable security.
Hence, the goal of this password checker is to help children form good security habits when making passwords (the foundation of secure authentication online) through a child-friendly manner for a better user experience.

This proactive password checker is designed to act as a stand-alone service, where children can instantly gain feedback on their password security.
This feedback will include not just security recommendations, such as avoiding common passwords etc., but also usability recommendations, such as a warning for a long password that may be too hard to remember.
Along with the password recommendation information located below the password text box, these usability recommendations shall hopefully discourage bad security habits, such as writing passwords down if the password is too long to remember.

Furthermore, as this is a password checker for minors, it is vital to effectively communicate feedback in a child-friendly manner that avoids too many confusing and technical terms that may intimidate a child.
Instead, feedback should be concise, clear and simple.
Also, it is well known that children typically have a shorter attention span than adults.
Therefore, it is not acceptable to rely on static written rules when trying to motivate a minor to develop a secure password.
As a result, the feedback should be instantaneous and dynamic as the user is typing to further enable interactivity and promote a subconscious reinforcement of good security practices.

#### User Interface

Particular care was taken when designing a clear and usable interface.
The following criteria were taken into account:
* Varying the importance and criticality of respective communications with the user.
* Clarity and readability of any communication with the user.
* Ease of interaction with any provided functionality.

Messages that we show to the user must be easily understandable to young children so that even the youngest users are kept in-the-loop on the features that define a secure password.
To do this we used encouraging and straightforward language in all of our messages, taking care to avoid technical terms like ‘special characters’ or ‘upper-case’ and complex words like ‘combination’.
We also decided that colours were a suitable way of emphasising suggestions to aid communication, using the ‘red is bad, green is good’ colour scheme.
One example of this is the messages beneath the password input, which range from bright red to bright green, directly communicating the scale of password strength to the user in a clear and intuitive way.

Additionally, precautions have been taken not to clutter the interface with information.
There are many standards and guidelines for creating a strong password, but showing them to the user all at once would only distract them from the task.
When using the password checker, the user is presented with a simple username and password input, and a condensed list of five basic requirements for a good password.
This ensures the user is given at least the basic knowledge they require to start working on a password while not flooding them with so much information that they don’t know where to start.

By checking the boxes next to each requirement and counting the number of requirements met, this adds a fun gamified element to creating a secure password.
By challenging the user to meet as many requirements as possible, the user is encouraged to make a secure password without explicitly telling them they must use certain features to be secure.
A user doesn’t need to meet every requirement for their password to be classified as strong, because explicitly enforcing too many rules may discourage the user.
Instead, while meeting 3 out of 4 of the requirements gets the user a strong password, they’re still encouraged to improve it to get the maximum score.

As each requirement is met, a green tick is displayed next to it, and once they’re all satisfied, the score turns green too.
This is in keeping with the colour scheme used to convey password strength to not confuse the user.

#### Assessing Password Strength

When assessing password strength, both technical factors and usability factors were considered.
However, before the password strength could be evaluated, the checker first checks for the absence of fundamental security flaws.

For example, if an entered password is shorter than 8 characters, a message encouraging the use of more characters is displayed, as recommended by [NIST guidelines](https://pages.nist.gov/800-63-3/sp800-63b.html#sec5).
Conversely, if an entered password is longer than 32 characters (a difficult length of password for a child to remember), a message warning of its length is displayed.
This message hints that the password, although being potentially very secure, may be too difficult to remember, hence, it also discourages the extremely insecure practice of writing passwords down.

If the entered password matches a password from the [SecLists set of common passwords](https://github.com/danielmiessler/SecLists), a warning message is displayed.
There is a function in the [script.js](script.js) file that looks for these common passwords.
We use a trie data structure that means even if our list of common passwords is thousands of entries long, lookup is perceptually instant.

If common number-letter replacements are used to replace certain letters within the common passwords with numbers (e.g. ‘5’ replacing ‘s’), the warning message stating 'Replacing letters with numbers isn't enough ;)' is displayed.
Again, there is a function in the [script.js](script.js) file that looks for these common number-letter replacements.
These number-letter replacements want to be avoided as they are a well known tactic in password creation that can be exploited by attackers.

Once these basic flaws are confirmed to be non-existent, the strength of a password is calculated.
Initially, before checking, the strength of a password is assumed to be 0.
From that baseline, the final strength is then determined by the presence of the following properties within the password:
* If an entered password is 8 characters or longer, the password strength is increased by 1.
* If an entered password contains a mixture of lower and upper case characters, the password strength is increased by 1.
* If an entered password contains a mixture of alphabetic characters and numeric characters, the password strength is increased by 1.
* If an entered password contains a mixture of alphanumeric characters and special characters (symbols such as !@£ etc.), the password strength is increased by 1.
* Finally, if an entered password contains at least two special characters, the password strength is increased by 1.

As an added precaution, users are able to enter their username as well as their password.
This lets our application check for the similarity between the two.
Within the [script.js](script.js) file, we’ve implemented a longest common subsequence algorithm that allows us to compare the username string and the password string.
If a username and password are more than 50% similar (contain more than 50% of the same characters in the same order) the following message is shown: 'Your password is very similar to your username'.

#### More information and more details on evaluation of the application are contained in the [report](Report.pdf).
