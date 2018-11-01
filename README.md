# # Project 8 - Pentesting Live Targets

Time spent: 5 hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

- Username Enumeration
- Insecure Direct Object Reference (IDOR)
- SQL Injection (SQLi)
- Cross-Site Scripting (XSS)
- Cross-Site Request Forgery (CSRF)
- Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection
The site with this vulnerability was blue. Starting at the same point as the previous vulnerability, you can replace the ‘id=??’ with not a number,but with an SQL code. For this application, I used, ' OR SLEEP(5)=0--'. What this does is it halts the loading of the page for 5 seconds. After putting in this command, the page took longer than usual to load, indicating that the attack was successful.
GIF Walkthrough: ![alt text](https://github.com/c-ryan-jung/codepathlabWeek8/blob/master/SQLi.gif)

Vulnerability #2: Session Hijacking/Fixation
The site with this vulnerability was blue. To do this two different browsers were used (firefox and chrome). First we normally logged in with the Firefox browser. We then used the tool provided by Code path to get the SESSIONID. Next we went to the chrome browser and using the same tool, we changed the SESSIONID to the one we had before. This allowed us to log in without the need for a password.
GIF Walkthrough: ![alt text](https://github.com/c-ryan-jung/codepathlabWeek8/blob/master/SessionHijacking.gif)

## Green

Vulnerability #1: Cross-Site Scripting
The site with this vulnerability was Green. On the contact us page, there are a couple of forms that someone can fill out. For our purposes we can put in a script that prompts a javascript alert. I will be using <script>alert(‘gotcha’)</script> This won’t activate immediately, but one someone logs in and checks the feedback page, the script will run and the javascript alert will be activated, letting us know of a successful XSS attack.
GIF Walkthrough: ![alt text](https://github.com/c-ryan-jung/codepathlabWeek8/blob/master/XSS.gif)

Vulnerability #2: Username Enumeration
The Site that had this vulnerability was Green. One could tell whether or not a username was correct based on the response the webpage gives after an incorrect password attempt. While the responses might look the same, when the correct username was input, the message was bolded but when an incorrect/non-existing username was put in, the message was not bolded, thus letting an attacker know of the existence of a username.
GIF Walkthrough: ![alt text](https://github.com/c-ryan-jung/codepathlabWeek8/blob/master/userenum.gif)

## Red

Vulnerability #1: Insecure Direct Object Reference
This vulnerability was found in the Red site. When looking through the Salespeople list, I found that in the URL, the pages were denoted by an ID number (ID=??). With this I can access information that wasn’t available or wasn’t supposed to be seen by the public eye.
GIF Walkthrough: ![alt text](https://github.com/c-ryan-jung/codepathlabWeek8/blob/master/IDOR.gif)

Vulnerability #2: Cross-Site Request Forgery
The site with this vulnerability is Red. This one involves a bit of social engineering. First an html page is created that has a hidden form. Then we entice an admin to check out the page we created by submitting it as a feedback post. The admin will be met with a blank html page, but back at the salesmen page, we notice that information has been changed around.
GIF Walkthrough: ![alt text](https://github.com/c-ryan-jung/codepathlabWeek8/blob/master/CSRF.gif)

## Notes

This lab really required me to look back and utilize everything we've learned so far. It definitely was not easy.
