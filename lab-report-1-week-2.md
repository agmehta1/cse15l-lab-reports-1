# Week 2 Lab Report
## This report includes the steps I took to complete the week 1 lab. All of these steps will be the steps required for Windows users.

### 1. Setting up VsCode

* Download VsCode using this [link](https://code.visualstudio.com/download)

* Once VsCode has been downloaded, open up the program. You should see a window like this 
![Image](lab-report-1-ss/VsCode_ss.png)

* Click on the extensions tab on the left side of the window. It is the image on the bottom with the foru squares.

* Search "java" in the search bar and install the "Extension Pack for Java" and "Debugger for Java" if they are not already installed. You may also install any other extensions that you would find useful.

![Image](lab-report-1-ss/VsCode_ext_ss.png)

* Now that VsCode has been setup, we can move onto connecting through ssh.


### 2. SSH

* Install OpenSSH following the instructions at this [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse#install-openssh-using-windows-settings)

* Next we will have to look up our CSE15L account at this [link](https://sdacs.ucsd.edu/~icc/index.php)

![Image](lab-report-1-ss/Account_lookup_ss.png)

* Fill in your username and Student ID in the first two options and click submit.

* Click on the account beginning with cs15l

* You will have to change your password for this account. Many students (including me) had issues with this step. One tip that worked for me was to select the yes option in the "*Change MyTritonLink password*". It will likely take a while before you password is actually updated, so wait around 15 mins before moving onto the next step.

* Once you have succefully changed your password, open up VsCode and click on *Terminal* in the top bar.

* Click on *New Terminal*

* In the terminal type in the following command filling in your unique account but including the @ and everything after.
`ssh UniqueAccount@ieng6.ucsd.edu`

* You may or may not get a warning message when you first try this command. Type `yes`.

* The terminal will ask for your password. Your password will not show as you type. Enter your password, and if your connection was successful you will see something like this.

![Image](lab-report-1-ss/ssh_connected_ss.png)

* You are now connected to the remote server. If the terminal asks for your password again after you pressed enter, this means that you passsword was incorrect. Mkae sure you are typing your password correctly. 

* If you are sure that you have typed your password in correctly, you should either try again later to see if your password change had not gone through yet or reset your password again.

### 3. Running commands

* In this step you can experiment with running various commands on the remote server.

* Try running these commands 
`cd`, `ls -lat`, `ls -a`

* This is what I see using `ls -a`
![Image](lab-report-1-ss/ls_a_ss.png)

* If you would like to close your connection, either enter "exit" into the terminal or use the command "Ctrl+D". Your connection will automatically be terminated after a while as well.

### 4. Scp

* In this step we will be using scp to move a file to the remote server. 

* Create a new file in Vscode called WhereAmI and copy the following program.

```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
#### Steps to create a file in VsCode
* Starting from the Get Started window you can click on "explorer" on the right. It is the icon with two pages.

* Create a Java Project with no build tools and save the folder. 

* Open the folder and create a new file with the above program.

* Save the file and right click on the name of the file in the explorer tab. Click on "Open in integrated terminal".

* Similarly to the process for ssh, enter in the following command. Enter in your password when prompted.
`scp WhereAmI.java UniqueAccount@ieng6.ucsd.edu:~/`

* This is what I see.

![Image](lab-report-1-ss/scp_ss.png)

* Now relog into ssh and type in the command `ls`. The file should be there and you should be able to run `javac WhereAmI.java` and `java WhereAmI`.

### 5. SSH Key

* To create a ssh key, run the following command in your own computer's terminal(For windows search cmd in the searchbar).

`ssh-keygen`

* fill out the answers to the terminal prompts. For the file you can just press enter to use the default file name.

* This is what I see after running the command. 
![Image](lab-report-1-ss/ssh_key_ss.png)

* Now back in VsCode ssh back into your account and run:

` mkdir .ssh`

* logout by typing "exit" and run:

`scp /Users/your_username/.ssh/id_rsa.pub UniqueSSHAccount@ieng6.ucsd.edu:~/.ssh/authorized_keys`

* Now retry logging into the remote server.

### 6. Optimizing Remote Running

* Try out some commands that simplify the remote access process.

* Try including commands in quotes after your ssh command, such as:

`ssh UniqueAccount@ieng6.ucsd.edu "ls"`

* This is what I see.
![Image](lab-report-1-ss/ls_ss.png)

* Try running multiple commands by separating the commands with semicolons

`cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI`

* This is what I see.
![Image](lab-report-1-ss/cp_ss.png)

* Try using the arrow keys to reuse a command you have typed earlier.

You have completed the lab.