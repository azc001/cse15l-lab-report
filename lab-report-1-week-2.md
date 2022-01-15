# Week 2 Lab Report
`By Andrew Chen`

This is a tutorial for incoming CSE 15L students and my future self on how to log into a course-specific account on `ieng6`.

## Installing VSCode

![img1](images\lab-report-wk-2-1.png)

Go to the [Visual Studio Code website](https://code.visualstudio.com/) and follow the instructions to download the correct version for your OS. Once downloaded, open the installer to set it up on your machine. After some time, it should be installed and ready to go. You can find it by searching "vsc" on the taskbar if you don't have a shortcut made.

## Remotely Connecting
If you're on Windows, first navigate to **Settings > Apps > Apps & Features > Optional Features**. Make sure you have OpenSSH installed by searching "ssh" in **Installed features**. If you are missing **OpenSSH Client** or **OpenSSH Server**, obtain the missing app by clicking on **View features**.

![img2](images\lab-report-wk-2-2.png)

Find your course-specific account for CSE 15L on the [UCSD account lookup site](https://sdacs.ucsd.edu/~icc/index.php) and set your password if you don't know the account's password. For this course, the account email should resemble something like `cs15lwi22aek@ieng6.ucsd.edu`. Then, go to Visual Studio Code and enter the command `$ ssh cs15lwi22aek@ieng6.ucsd.edu` in a new terminal, replacing the email with your course-specific account's ($ just represents anything that comes before the command such as the file path). Type yes if it prompts you if you want to continue connecting and then enter your password (which will be hidden). If your password is entered correctly, you will be welcomed with some text that shows you your CPU usage on the system.

![img3](images\lab-report-wk-2-3.png)

## Trying Some Commands

![img4](images\lab-report-wk-2-4.png)

Now that you are remotely connected, you can try running some commands on the remote computer through the Visual Studio Code terminal. Some commands you can try are `cd ~`, `cd`, `ls -lat`, and `ls -a`. You can close the remote connection by pressing *Ctrl-D* or running the command `exit`.

## Moving Files With `scp`
In the top left corner of Visual Studio Code, press **File > New File** (or use the hotkey *Ctrl+N*). Name the file `WhereAmI.java` and paste the following code into it.

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

Save the file and try running it with `javac WhereAmI.java` and `java WhereAmI` commands. Then, in the terminal using the directory of the file's location (on the client), run `scp WhereAmI.java cs15lwi22aek@ieng6.ucsd.edu:~/` with your own account. If you relog into the remote computer with `ssh`, you should be able to see it on the directory with the `ls` command and be able to run it remotely with `javac` and `java`.

![img5](images\lab-report-wk-2-5.png)

## Setting an SSHKey
In order to make remote connecting easier, we're going to create a pair of SSH keys (a public one on server and a private one on our machine) to make life easier, which will be used in place of our password. Run the command `ssh-keygen` on your client and follow the prompts. 

![img6](images\lab-report-wk-2-6.png)

Since we're on Windows, we will need to follow [extra steps](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation). Open the taskbar and navigate to **Services > OpenSSH Authentication Agent** and change the **Startup type** to **Manual**. Run the commands `Start-Service ssh-agent`, `Get-Service ssh-agent`, and `ssh-add <SSHKey file location>` on the client to make the ssh-agent automatically retrieve your local private key whenever a private key is needed for authentication.

![img7](images\lab-report-wk-2-7.png)

Then, to copy the public key to the remote computer, log on using `ssh` and run the command `mkdir .ssh`. Logout and run `scp \Users\andrz/.ssh/id_rsa.pub cs15lwi22aek@ieng6.ucsd.edu:~/.ssh/authorized_keys` on your client (replacing the first parameter with the file path for your SSH key and the second with your own course-specific account), using the `scp` command demonstrated earlier to copy the key to the remote computer. 

![img8](images\lab-report-wk-2-8.png)

After doing this, you should be able to connect using `ssh` on your computer without using a password.

![img9](images\lab-report-wk-2-9.png)

## Optimizing Remote Running
Now that we've learned all the basics, we can combine the past commands used in this tutorial with some new tricks to optimize the way we connect and copy files to the remote computer. For example, you can write a command in quotes at the end of an `ssh` command to run it on the remote server, or you can use semicolons at the end of commands to run multiple commands on the same line. The up-arrow key can also be useful in copying the last ran command.

![img10](images\lab-report-wk-2-10.png)