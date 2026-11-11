# Password cracking with the tool John the ripper
## What is password hashing?
  Password hashing means turning a real password into a scrambled text. Websites store this scrambled text instead of the real password. So even if an attacker gets into the database, they only see scrambled characters, not the actual raw passwords
  Hashing is usually done using a method called SHA-256 its basically an algorithm . This method takes any text and turns it into a fixed scrambled code. Many websites use it because it's fast and hard to reverse. Means reverse engineering cannot be done after it's hashed.
 # Salting :
 Is method of assigning random unique piece of text called 'salt' added to a user's password before it gets hashed. Why do we actually need it? If two users have the exact same password like apple123, the normal hash turns them into the exact same output. Salting gives every single user a completely different random salt during their final codes are totally unique
- Before salt
  
|   Name |Raw password | Hashed password                   |
|--------|-------------|-----------------------------------|
| Alice  | Dragon26    |  c7f2a1b9e8d4c6035a7f0b2e9d1c846a |
| John   | Dragon26    |  c7f2a1b9e8d4c6035a7f0b2e9d1c846a |

   The attacker could crack one password and exploit many of them who have similar passwords
   
- After salt
  
|   Name |Raw password + Salt | Hashed password                     |
|--------|--------------------|-------------------------------------|
| Alice  | Dragon26 + "x7k9"  |  ef526twgyetygdyueyuyey35667gqwwhdg |
| John   | Dragon26 + "m2p4"  |  bs53723dghwtvdftddghaede7e36bebdi9 |

Now we gave extra work for the attacker .They should match the salt with each password to find matches. Really a tough task, But that doesn't mean u are really really that far from being cracked. Still the password can be cracked with a powerful tool called "john the ripper" &  the attacker have to really really lock in too.


# How I Cracked My Own Password
### AKA: Is your password already in a hacker's list? Lets find out
### DICTIONARY ATTACK:A dictionary attack uses a list of possible passwords, hashes each guess, and compares the results against stolen password hashes to find a match."

-⚠ NOW THIS IS JUST A PLAY TO ACTUALLY KNOW HOW THIS TOOL WORKS. THIS WAS NOT DONE AGAINST A REAL DATABASE

1] open your linux terminal & create a imaginary stolen database 
   - create  two files inside a directory using command  "touch <filename>" create two files seperately eg; touch password.txt & Hashed passwrod.txt voila u just created a file  .Now to actually verify if that file is created command "ls" and u can see the file u made listed.
   - open that file(password.txt) in a nanoeditor command "nano <filename>" now u can actually type or edit anything u want . Now i want u to write some similar  password line by line(vertical) u know eg: "password123", "monkey" "iloveyou" anything u want including ur own password i did write my own password & learnt my lesson. After writing the passwords save it .To save it in Press "ctrl+o"(saves)  & enter "ctrl+x (exits from nano).
   - now to open the file u mad and to see all the passwords u mad command  "cat <filename>" cat password.txt & u can see all the password u wrote.
   - lets hash it, because the stolen database will be in hashed form reminder "our imaginary stolen database is not salted passwords" we will do that later . For hashing, Note: SHA-256 is the hashing algorithm. sha256sum is the Linux tool that runs it. Now if u type "sha256 sum <filename>"  it will hash everything in that file together. so we are going to perform a loop that is gonna hash each line command [while read -r variable; do echo -n "$variable" | sha256 sum | awk '{print $1}' >> Hashed password.txt; done < password.txt ]
   - after u typed the command it hashes the password.txt file and save into hashed password.txt
   - type cat Hashed password. txt to see if it saved the hashed passwords into the file.
   - now our imaginary stolen database is ready.
     
 2]   Time to use john the ripper tool
  - type command "locate rockyou.txt"  it will show like 'usr/share/wo rdlists/rockyou.txt' which is famous for its  breach list for having all kinds of passwords . Reminder: Do not "cat rockyou.txt" because it will flood your terminal coz it has a millions of passwords
  - before that we have to decompress the file type  "sudo gzip -dk /usr/share/wordlists/rockyou.txt.gz" this command helps you to decompress the file and let u peek inside the file
  - if u really wanna peek inside rockyou.txt use commands like
       1] head -n 10 /usr/share/wordlists/rockyou.txt". To view only first ten passwords
       2] less rockyou.txt .if u wanna inspect interactively line by line use down arrow key to scroll down. To exit press "q"
   # now its time,  lets see how much passwords we can actually crack
   - john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-sha256 sunshine
    
   ## what it actually does
  - john : This just runs the John the Ripper program itself.
 -  --wordlist=/usr/share/wordlists/rockyou.txt : This tells John: "use this file as your guessing dictionary." You're pointing it to rockyou.txt — the list of real leaked plain-text passwords. John will try each one, one by one, as a guess.
- --format=raw-sha256 : This tells John: "the hashes in my target file are SHA-256 type." This matters because John needs to hash its guesses the same way your hashes were made — otherwise even the correct password would produce a different-looking hash and never match. Since you hashed with sha256sum earlier, this flag has to match that.About sha256sum not being in the John command 


Putting it together: "John, take every password in rockyou.txt, hash each one using SHA-256, and check if it matches any of the hashes sitting in my sunshine file. Tell me when you find a match.

 ## you can see the cracked passwords, yea john just did that in seconds probably not even seconds faster than that . Yes my password was also cracked i understood how vulnerable my password was and immediately changed it was yours cracked  LMK. Now i know why google suggest me gibberish passwords . Please keep a long passwords something like a sentence which is emotionally connected to you jk   
       
      
