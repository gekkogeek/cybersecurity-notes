# How i connected to HTB labs
( I Have already setup  linux environment in my computer so all the browsing was done in linux itself)

- step1:  Go to the HTB labs u wanna access & download an openvpn file

- step2: To verify that the file is download. Open the linux terminal & type the command
 "pwd" to see your exact location in the terminal. If it shows (home/username), your in the home directory. if ur not, just type "cd" command to take you inside home directory. Next type " ls " command to list all the directories in the home directory. Now u can see so many directories like downloads,documents,etc. The downloaded ovpn file will be probably inside download directory to get inside the download directory ,type "cd Downlaods " command and enter. Now ur inside the downlaod folderor directory same things to list whats inside the download directory type "ls" u will see an ovpn file inside . now that u made sure its downloaded its time to connect to that file via OPENVPN

- step3: install openvpn package inside linux terminal
## whats a OPENVPN PACKAGE
     Its a universal software tool used to create secure connections across many different private networks. Basically it builds a secure tunnel for ur data to travel safely. connecting to a private network requires a specific ovpn file to grant entry.
   Type "sudo apt install openvpn" in ur terminal  (sudo apt install <filensme>)
   sudo =  runs the commands with administrator privileges 
   apt = 'the package manager'that automatically loactes & downloads software from official linux repositories. linux repositories is simply a playtsore in linux.
    To ensure  its installed type "openvpn --version" if its success u can see the version pop up
    - step 4: connect the file. type "sudo openvpn <.ovpnfile>" enter type ur password enter , if u can see the line 'Initialization sequence completed 'congratulations ur  successfully tunnel into the HTB labs network .now u have connection with the  htb server .
