1. Deploy your AttackBox (the blue "Start AttackBox" button) and the tasks machine (green button on this task) if you haven't already. Once both have deployed, open FireFox on the AttackBox and copy/paste the machines IP (10.10.229.142) into the browser search bar.
  - Answer: Click the submit button.


2. Given the URL "http://shibes.xyz/api.php", what would the entire wfuzz command look like to query the "breed" parameter using the wordlist "big.txt" (assume that "big.txt" is in your current directory)
  - Answer: `wfuzz -c -z file,big.txt -u http://shibes.xyz/api.php/?breed=FUZZ`
  - Explanation: I originally thought the answer would be `wfuzz -c -z file,big.txt -d "breed=FUZZ" -u http://shibes.xyz/api.php` due to the provided examples where it shows the fuzzing parameters being inserted before the main URL. The answer format gave me the hint I needed after getting errors with the submission. Both versions of the command work, however.
  
  
3. Use GoBuster to find the API directory. What file is there?
  - Answer: `site-log.php`
  - Explanation: Use the tutorial to assemble your command. Here is mine: `./gobuster dir -u http://10.10.229.142/ -w ~/CTF_Workspace/Word\ Lists/Enumeration/big.txt -x php,txt,html`. This will take some time if you have a slower CPU, thankfully you inly have to wait until around 14 percent completion. Spoiler alert, the API directory is called `api` if you want to skip ahead.

  
4. Fuzz the date parameter on the file you found in the API directory. What is the flag displayed in the correct post?
  - Answer: `THM{D4t3_AP1}`
  - Explanation: Using `wfuzz --hh 1 -z file,wordlist http://10.10.229.142/api/site-log.php/?date=FUZZ`, I get a list of responses. One of them, `20201125`, returns a 1 word reply of 13 characters. `http://10.10.229.142/api/site-log.php/?date=20201125` and we get our key.
  
