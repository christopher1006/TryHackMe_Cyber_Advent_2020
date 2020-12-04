You have been assigned an ID number for your audit of the system: `ODIzODI5MTNiYmYw` . Use this to gain access to the upload section of the site.


1. What string of text needs adding to the URL to get access to the upload page?
  - Answer: `?id=ODIzODI5MTNiYmYw`
  - Explanation: Going straight to the web page by plugging in the IP doesn't fully work. A splash page comes up with a notice that you are not signed in, saying `Please enter your ID as a GET parameter (?id=YOUR_ID_HERE)`. Presumably, this is a reference to that ID number string from the dossier; so it's worth starting there. The resulting input for me was `http://10.10.205.62/?id=ODIzODI5MTNiYmYw`. Note that I did not put the `/` after the IP address but Firefox fixed it for me. 

2. What type of file is accepted by the site?
  - Answer: `Image`
  - Explanation: Alright, now we're in and there's a warning about suspicious persons with a file upload service. Instead of trying to find a bunch of files to throw at this thing, let's first check the source code and see if anything interesting pops up. Jackpot! Line 22 says `<input type=file id="chooseFile" accept=".jpeg,.jpg,.png">`. Now we know what the file uploader is accepting, what do these files all have in common? They're image files, so let's trying `Image` and it works.

3. Bypass the filter and upload a reverse shell. In which directory are the uploaded files stored?
  - Answer: `/uploads/`
  - Explanation: Using the provided php reverse shell, there has to be some way to load it onto the server. The tutorial mentioned a method of attack where you prepend the extension with an allowed file format. I tried `php-reverse-shell.jpg.php` and the file uploader took it. As a note, when I was looking for the file to submit, it did not show up on the accepted types filter. Just change to all file types, select the file, and the uploader will still take it. To find the directory, I just typed in some of the example directories from the dossier and uploads worked, showing a file listing.

4. Activate your reverse shell and catch it in a netcat listener!
  - No answer needed, click to complete the task.
  - Explanation: Use the netcat command from the dossier to listen for connections on port 443 from any ip address. Click the php script in the uploads directory to start the reverse shell connection.

5. What is the flag in /var/www/flag.txt?
  - Answer: `THM{MGU3Y2UyMGUwNjExYTY4NTAxOWJhMzhh}`
  - Explanation: The question pretty much says it, `cat /var/www/flag.txt` for a message with the flag at the end.
