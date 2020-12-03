Day one is pretty much just a tutorial so I'll run through the list of tasks

1. "Deploy your AttackBox (the blue "Start AttackBox" button) and the tasks machine (green button on this task) if you haven't already. Once both have deployed, open FireFox on the AttackBox and copy/paste the machines IP into the browser search bar." - 
          Answer -  `Submit without filling the answer box`

2. Register for an account, and then login. What is the name of the cookie used for authentication? - 
          - The username needs to be at least four characters, the password needs to be at least 5 charaters. 
          - Inspect the webpage using your browser development tools and find where it lists cookies. 
          Answer - `auth`

3. In what format is the value of this cookie encoded?
          Answer - `hexadecimal`
          You can guess this due to the usage of 1-9 and a-f together.


4. Having decoded the cookie, what format is the data stored in?
          Answer - `json`

5. Figure out how to bypass the authentication. What is the value of Santa's cookie?
          - Open up cyberchef or your utf8-hex converter of choice and decode the hex value of `auth`. change the user to santa and encode the text back to hex.
          - Open your browser development tools back up by inspecting the page. Go to storage options and find the `auth` cookie. It should be the only one there. Double-click the value and replace it with the updated hex value that represents the santa user.
          Answer - `7b22636f6d70616e79223a22546865204265737420466573746976616c20436f6d70616e79222c2022757365726e616d65223a2273616e7461227d`

6. Just click the selection sliders and the flag pops up at the bottom
          Answer - `THM{MjY0Yzg5NTJmY2Q1NzM1NjBmZWFhYmQy}`
