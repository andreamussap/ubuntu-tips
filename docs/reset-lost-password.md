# Ubuntu - How to reset a lost *root* password
You know when you write down a password and keep it so carefully that you can't find it anymore?? That happened to me! As a result, I couldn't perform any administrative task on Ubuntu because every time I tried it, it asked me for the *root* password.

So, I searched for articles on how to reset my Ubuntu password and I found uncountable results. However, none of them alone could help me, so I had to gather parts of the articles to troubleshoot my own problem.

In this article I'll describe the step-by-step I used to reset my Ubuntu password, and I hope it's of sufficient help for you not having to consult different websites at the same time.

# Issue
I forgot my Ubuntu *root* password

# Troubleshoot
How to reset Ubuntu *root* password

# Ubuntu version
16.04 LTS

# Tips
This tutorial will reset Ubuntu *root* password, that is, you don't need to remember your current password because it'll overwrite it.

# Steps

###1. Turn on or reboot your computer to access the [GRUB] menu.

- If Ubuntu is your only installation keep pressing the left SHIFT key after starting the computer until GRUB's menu appears.
- As I have a dual-boot, the GRUB is displayed automatically to me. 

![](/docs/images/01-grub-start.jpg)

###2. Open the GRUB Menu in edition mode to update it.

Highlight the **Ubuntu** menu item and type **'e'** to edit it.

![](/docs/images/01-grub-menu-edition.jpg)

###3. Look for the line starting with *linux* and add *init=/bin/bash* to its end.

`linux (...) ro  quiet splash $vt_handoff init=/bin/bash`

###4. boot directly into root shell prompt without password.

`Press Ctrl+X`

###5. Once in root shell, remount Ubuntu system with read and write permission:

`mount -rw -o remount /`

###6. List the username if you forgot it:

`ls /home`

###7. To reset the password type:

`passwd <USERNAME_LISTED_ABOVE>`


*Here is a complete example on how to remount the filesystem and reset the password for the user *ml*.*

![](/docs/images/04-reset-password.jpg)

###8. Finally, reboot the system and try any administrative task to test your new password.

`exec /sbin/init`



[GRUB]: https://www.gnu.org/software/grub/
