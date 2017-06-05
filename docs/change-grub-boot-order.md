# Ubuntu - How to change GRUB boot order

I have [dual-boot] system on my computer which starts **Ubuntu** by default, and I want to change the [GRUB] boot default to **Windows**. For that, we're going to update the `GRUB_DEFAULT` parameter value in the **grub** file via command line.

> This procedure won't change the order of the GRUB's list, it will allow a different OS to boot by default.

# Ubuntu version
16.04 LTS

# Prerequisites
- From the GRUB list, write down the order of the SO you want to boot by default. (The ordered list starts from **0**)

![](/docs/images/boot-order-01.jpg)

- Ubuntu **root** password is known.

> If you have lost the **root** password, refer to **Ubuntu - How to [reset] a lost *root* password** article to know how to reset it.

# Steps

**1.** Turn on or reboot your computer to access Ubuntu.

**2.** Open the *terminal* from App Launcher, or via **Ctrl + Alt + T** keys.

![](/docs/images/boot-order-02.jpg)

**3.** Create a backup of the **grub** configuration file:

`sudo cp /etc/default/grub /etc/default/grub.bak`

**4.** Open the configuration file to edit it:

`gksudo gedit /etc/default/grub`

> If you don’t have gksudo installed, install it by typing: sudo apt install gksu

**5.** In the **grub** file, look for the line that contains `GRUB_DEFAULT=0` and set it to `GRUB_DEFAULT=saved`.

**6.** Save and close the file.

**7.** Go back to the *terminal* and update grub to apply the changes:

`sudo update-grub`

**8.** Set the default boot OS:

`sudo grub-set-default <NUMBER>`

**9.** Close the *terminal*

`exit`

**10.** Reboot your computer to test the procedure.

[dual-boot]: http://searchwindowsserver.techtarget.com/definition/dual-boot
[reset]: https://github.com/andreamussap/ubuntu-tips/blob/master/docs/reset-lost-password.md
[GRUB]: https://www.gnu.org/software/grub/
