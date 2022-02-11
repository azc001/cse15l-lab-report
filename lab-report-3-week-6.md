# Week 6 Lab Report 3
`By Andrew Chen`

This lab report details how I went about streamlining ssh configuration to make logging in a much easier process.

First, I created the .ssh/config file by using the following commands.

```
cd %HOMEPATH%/.ssh
type nul > config
```

This created a config file in my .ssh folder, which I then opened in Visual Studio Code.

![img1](images\week-6\img1.png)

I pasted in the section of code on the lab website and inserted my username `cs15lwi22aek`. After saving the config file, I was able to login to my course-specific account on the remote server by just running `ssh ieng6`.

![img2](images\week-6\img2.png)

This makes accessing the remote server a lot simpler, as I don't have to type out the full `ssh cs15lwi22aek@ieng6.ucsd.edu` everytime I want to login. `ssh ieng6` is a lot easier to remember and saves a lot of time.

![img3](images\week-6\img3.png)

This also allows me to copy over files faster by just using `ieng6` instead of the whole account name.