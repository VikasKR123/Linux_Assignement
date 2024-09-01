<h1>Create a user in your localhost, which should not be able to execute the sudo
command.<h1>

<h4>
<ul>
  <li>Use the adduser command to create a new user. For example, let's create a user named vikas.</li>
   <p>sudo useradd vikas<p>
  <li>By default, new users are not added to the sudo group, which is the group that grants the ability to use sudo.</li>
  <li>To verify that the user cannot execute the sudo command</li>
  <li>
   <ol>
      <li>Switch to the new user</li>
      <p>su - vikas </p>
      <li>Try to run a command with sudo, such as</li>
      <p>sudo ls /root</p>
      <li>It shows:  vikas is not in the sudoers file.  This incident will be reported.
 </li>
   </ol>
</li>
</ul>
</h4>

![A2](https://github.com/user-attachments/assets/fcf180e9-0385-4b7f-942b-31c26d7c1b3e)



-----------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1>Configure your system in such a way that when a user type and executes a describe command from anywhere of the system it must list all the files and folders of the user's current directory.</h1>

<p><b>Step 1: </b>Move to the root directory and edit the /etc/bash.bashrc file to add a global alias.</p>
<p><b>Step 2: </b>Save the changes to the /etc/bash.bashrc file.</p>
<p><b>Step 3: </b>Reload the terminal to apply the changes. </p>
<p><b>Step 4: </b>After Reloading then enter ‘describe’ in the terminal then it shows current directory file</p>

![A32](https://github.com/user-attachments/assets/f76ede5f-117b-45a1-852d-48a4e36f73dc)

![A24](https://github.com/user-attachments/assets/e9c46434-1376-41d1-96bc-b9796671ba88)

![A31](https://github.com/user-attachments/assets/95590e31-90be-4548-b95b-1b256dd72397)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

<h1> Users can put a compressed file at any path of the linux file system. The name of the file will be research and the extension will be of compression type, example for gzip type extension will be .gz.</h1>
  <h2>You have to find the file and check the compression type and uncompress it.</h2>
  
<p> 
<b>1.</b> First, create a file named research in your home directory<br>
<b>2.</b> Populate the research file with the output of the directory listing<br>
	  ls -ltr > research<br>
<b>3.</b>Next, create a directory called compres and then create a research file within that      n     directory<br>
<b>4.</b> Populate the research file inside the compressed directory with the directory listing<br>
<b>5.</b>Compress the research file in your home directory using gzip<br>
<b>6.</b>Update the permissions for the research.gz file to make it executable<br>
<b>7.</b> When you list the files with ls -ltr, the compresse file will be displayed as research.gz.<br>
<b>8.</b>To locate and unzip the research.gz file, you need to execute a script that finds the file and decompresses it.<br>
</p>
<pre>#!/bin/bash

FILE_NAME="research"

find / -type f -name "${FILE_NAME}.*" 2>/dev/null | while read -r COMPRESSED_FILE; do
    echo "Found compressed file: $COMPRESSED_FILE"
    
    # Determine the file type
    FILE_TYPE=$(file -b "$COMPRESSED_FILE" | awk '{print $1}')
    
    # Uncompress based on the file type
    case "$FILE_TYPE" in
        gzip)
            echo "Uncompressing gzip file..."
            gunzip "$COMPRESSED_FILE"
            ;;
        bzip2)
            echo "Uncompressing bzip2 file..."
            bunzip2 "$COMPRESSED_FILE"
            ;;
        XZ)
            echo "Uncompressing xz file..."
            unxz "$COMPRESSED_FILE"
            ;;
        Zip)
            echo "Uncompressing zip file..."
            unzip "$COMPRESSED_FILE" -d "$(dirname "$COMPRESSED_FILE")"
            ;;
        7-zip)
            echo "Uncompressing 7z file..."
            7z x "$COMPRESSED_FILE" -o"$(dirname "$COMPRESSED_FILE")"
            ;;
        *)
            echo "Unknown compression type: $FILE_TYPE"
            ;;
    esac
done

echo "Uncompression process completed."</pre>


![A42](https://github.com/user-attachments/assets/68521d3c-c606-45fb-85e0-d001bf18ec94)

![A43](https://github.com/user-attachments/assets/d405b5d5-a39e-4b80-b7f5-d386874ece77)



----------------------------------------------------------------------------------------------------------------------------------------------------------------

<h1>Configure your system in such a way that any user of your system creates a
file then there should not be permission to do any activity in that file.
Note:- Don’t use the chmod command.
</h1>

<h4>To achieve this, the user needs to add <b>umask 0777</b> to both their profile file and the global bash.bashrc file. Once these changes are made and saved, any newly created files will have no permissions by default.</h4>

<h4>We need insert -> umask 0777 for the highlighted files so that we can remove
the access permissions for the users.</h4>

<pre>
	sigmoid@sigmoid-ThinkPad-L470-W10DG:~$ sudo  nano /etc/profile
	sigmoid@sigmoid-ThinkPad-L470-W10DG:~$ sudo nano /etc/bash.bashrc
	sigmoid@sigmoid-ThinkPad-L470-W10DG:~$ nano ~/ .bashrc
	sigmoid@sigmoid-ThinkPad-L470-W10DG:~$ nano ~/ .zshrc
	sigmoid@sigmoid-ThinkPad-L470-W10DG:~$ source  ~/.zshrc
    		bash: /home/sigmoid/.zshrc: Permission denied
	sigmoid@sigmoid-ThinkPad-L470-W10DG:~$ touch vikas
	sigmoid@sigmoid-ThinkPad-L470-W10DG:~$ ls -ltr vikas

		---------- 1 sigmoid sigmoid 0 Aug 30 22:31 vikas
	sigmoid@sigmoid-ThinkPad-L470-W10DG:~$ 
</pre>

![A5](https://github.com/user-attachments/assets/2963b2a7-72d6-4dcc-9ce1-091c4fa3b1ad)

---------------------------------------------------------------------------------------------------------------------------------------------------------------


<h1>Configure SMTP in localhost</h1>

<pre>

<b>step 1.</b> Downloading sendmail
<b>step 2.</b> Install Postfix
<b>step 3.</b> Enable sendmail by using systemctl command
	
</pre>

<pre>

root@sigmoid-ThinkPad-L470-W10DG:/etc/mail# systemctl status  sendmail
● sendmail.service - LSB: powerful, efficient, and scalable Mail Transport Agent
     Loaded: loaded (/etc/init.d/sendmail; generated)
     Active: <font color="green"><b>active (running)</b></font> since Wed 2024-08-28 14:37:39 IST; 1min 18s ago
       Docs: man:systemd-sysv-generator(8)
    Process: 23891 ExecStart=/etc/init.d/sendmail start (code=exited, status=0/>
      Tasks: 1 (limit: 9272)
     Memory: 2.5M
     CGroup: /system.slice/sendmail.service
             └─24066 sendmail: MTA: accepting connections
</pre>

<pre>

root@sigmoid-ThinkPad-L470-W10DG:/etc/mail# mail -s "mail vikas" vikaskarbail@gmail.com
Cc: vikaskarbailkr@gmail.com
hello
hai

</pre>

<p>and then press ctrl+d then message is sent</p>


----------------------------------------------------------------------------------------------------------------------------------------------------------------

<h1>
<pre>
Create a service with the name showtime , after starting the service, every minute it should print the current time in a file in the user home directory.

Ex:-
sudo service showtime start   -> It should start writing in file.
sudo service showtime stop   -> It should stop writing in file.
sudo service showtime status -> It should show status.
</pre>
</h1>

<pre>
Login as root and create a directory in root
 # mkdir -p /usr/local/bin/showtime

Create the shell script file.
 # nano /usr/local/bin/showtime/showtime.sh
and then put the below content
</pre>
![Screenshot from 2024-08-30 23-03-07](https://github.com/user-attachments/assets/66e80762-4bd7-4a20-9b3a-ea3cdf463ec9)

<pre>
Create a service file named showtime.service.
  # nano /etc/systemd/system/showtime.service
Reload the service.
  # systemctl daemon-reload
Start the service.
  #systemctl start showtime.service

To check the status of the service.
  # systemctl status showtime.service
</pre>
![Screenshot from 2024-08-30 23-12-36](https://github.com/user-attachments/assets/bc35df12-8984-49c3-a278-f6cfa5a7c23e)

