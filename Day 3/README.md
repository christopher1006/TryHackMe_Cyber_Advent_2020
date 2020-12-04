1. Deploy your AttackBox (the blue "Start AttackBox" button) and the tasks machine (green button on this task) if you haven't already. Once both have deployed, open Firefox on the AttackBox and copy/paste the machines IP (MACHINE_IP) into the browser search bar.
   - Answer: Click complete when you have your attack box activated.

2. Use BurpSuite to brute force the login form.  Use the following lists for the default credentials:

Username 	Password

root 	root

admin 	password

user 	12345


Use the correct credentials to log in to the Santa Sleigh Tracker app. Don't forget to turn off Foxyproxy once BurpSuite has finished the attack!

What is the flag?
    - Answer: `THM{885ffab980e049847516f9d8fe99ad1a}`
   
   - Explanation: Follow the tutorial in the dossier and you will get the flag. Just make sure at the end to change the request username to `admin` and password to `12345` before forwarding it to the web server.
