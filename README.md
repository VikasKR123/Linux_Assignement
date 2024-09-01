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

![A31](https://github.com/user-attachments/assets/95590e31-90be-4548-b95b-1b256dd72397)





  
