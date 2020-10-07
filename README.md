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
