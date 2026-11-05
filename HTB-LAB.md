# How i connected to HTB labs
( I Have already setup  linux environment in my computer so all the browsing was done in linux itself)

- step1:  Go to the HTB labs u wanna access & download an openvpn file

- step2: To verify that the file is downloaded. First Open the linux terminal & type the command
 "pwd" to see your exact location in the terminal. If it shows (home/username), your in the home directory. if ur not, just type "cd" command to take you inside the home directory. Next type " ls " command to list all the directories inside home directory. Now u can see so many directories like downloads,documents,etc. The downloaded .ovpn file will be probably inside Downloads directory. To get inside the download directory ,type "cd Downlaods " command and enter. To see what's inside the download directory type "ls" u will see an ovpn file inside that u downloaded from the lab  .Now that u verified the file is there, its time to establish your secure connection using the .ovpn file.

- step3: install openvpn package inside linux terminal
## whats a OPENVPN PACKAGE
     Its a universal software tool used to create secure connections across many different private networks. Basically it builds a secure tunnel for ur data to travel safely. connecting to a private network requires a specific .ovpn file to grant entry.
   Type "sudo apt install openvpn" in ur terminal . (sudo apt install <package>) command helps to install any software in linux
   sudo =  runs the commands with administrator privileges 
   apt = 'the package manager'that automatically locates & downloads software from official linux repositories. Imagine linux repositories as a playtsore in android it has all the updated tools and softwares.
    To ensure  the package is installed. Type "openvpn --version" if its success u can see the version pop up
    
- step 4: connect the file. type "sudo openvpn <.ovpnfile>" enter .Type ur password enter , if u can see the line 'Initialization sequence completed 'congratulations ur  successfully tunneled into the HTB labs network .Now u have connection with the  htb server .
