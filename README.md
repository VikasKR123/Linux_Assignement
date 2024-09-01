<h1>Create a user in your localhost, which should not be able to execute the sudo
command.<h1>

<p>
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
</p>


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


![A42](https://github.com/user-attachments/assets/68521d3c-c606-45fb-85e0-d001bf18ec94)

![A43](https://github.com/user-attachments/assets/d405b5d5-a39e-4b80-b7f5-d386874ece77)





  
