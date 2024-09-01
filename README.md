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
