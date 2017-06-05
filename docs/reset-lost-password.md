# Ubuntu - How to Reset Lost Password
You know when you write down a password and keep it so carefully that you can't find it anymore?? That happened to me! As a result, I couldn't perform any administrative task on Ubuntu because every time I tried it, it asked me for the password.

So, I searched for articles on how to reset my Ubuntu password and I found uncountable results. However, none of them alone could help me, so I had to gather parts of the articles to troubleshoot my own problem.

In this article I'll describe the step-by-step I used to reset my Ubuntu password, and I hope it's of sufficient help for you not having to consult different websites at the same time.

# Issue
I forgot my Ubuntu password

# Troubleshoot
How to reset Ubuntu password

# Ubuntu version
16.04 LTS

# Tips
This troubleshooting will reset your Ubuntu password, that is, you don't need to remember your current password because it'll overwrite it.

# Steps

## 1. Turn on or reboot your computer to access the [GRUB] Menu

* If Ubuntu is your only installation keep pressing the left SHIFT key after starting the computer until GRUB's menu appears.
* As I have a dual-boot, the GRUB is displayed automatically to me. 

![](/docs/images/01-grub-start.jpg)

## 2. Access the Recovery Menu

From the GRUB menu, select option *Ubuntu*, and in the next window select the option with *(recovery mode)* in the description.

## 3. Recovery Menu options

![](/docs/images/01-recovery-menu.jpg)

**grub - Update grub boot loader**

Most of the articles I read tell you to select *root - Drop to root shell promt* option to reset the password. However, when I tried that I got this error:

> Authentication token manipulation error.

So, following another clue, before going to the ~~root - Drop to root shell promt~~ I selected the option *grub Update grub boot loader*, and on the screen bellow I selected *Yes*.

![](/docs/images/03-grub-update-grub-boot-loader.jpg)

> Note: You can try the *root - Drop to root shell promt* option first. If it works for you, great. If not, you can try the way I did.

**root - Drop to root shell promt**

When the system finishes the update above, go back to the *Recovery Menu* window, and select *root Drop to root shell promt*.

## 4. Command line actions

Now, you should see a prompt command line like this:

`root@(none):/#`

As the filesystem is read-only by default, you have to remount it with write permissions:

`mount -rw -o remount /`

*Pay attention to the spaces between the strings !!*

List the username if you forgot it:

`ls /home`

To reset the password type:

`passwd <USERNAME_LISTED_ABOVE>`

Example to remount the filesystem and reset the password for user **md**

![](/docs/images/04-reset-password.jpg)


[GRUB]: https://www.gnu.org/software/grub/
