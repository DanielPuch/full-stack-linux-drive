# Setting up your linux drive

## Booting with the USB

The USB drive we're supplying has a full bootable version of the Linux operating system. The version we are using on this drive is a customized version of Ubuntu. This drive is set up so that you can boot up your computer to run Linux right off of this drive without having to change your current operating system. This drive will not modify your current Windows or Mac installation. We've already set up the dev environment (rvm, ruby, rails, etc...) so you should be all set to start developing in a native environment.

First off, shut your computer down and plug in the USB drive. Now we're going to tell the computer to boot from the USB rather than the hard drive.

### If you're using a PC

Every computer is a little different in terms of what needs to be done to be able to boot up using something other than your hard drive. The goal here is to enter what is called the BIOS and change your boot order to boot from the USB drive. When your computer starts up, you usually get a black screen and for just a second and it will say something like `Press F12 to Choose Boot Device`. This is exactly what we want you to look out for. It sometime pops up quick so you may need to restart your computer to try and see it a second time. Once you find out what you have to press, you're going to want to press that key on start up and navigate through the menus to boot from your USB drive. If your windows desktop/login comes up, you did not trigger the boot device selection and you'll have to restart and try again.

If you don't see an option to choose your boot device, you can look for options to enter the BIOS. If you enter the BIOS, look through the settings for "Boot Device" or "Boot Order" (or something along those lines, again, every computer is different). In these menus you can select what order your computer checks to boot from. Use the Boot Order menu to set 'booting from a USB' _above_ 'booting from the HDD' (or Hard Drive). What this is telling your computer is to simply check to see if there is a bootable USB in a port before booting the operating system from the hard drive.

If you're not seeing any options when the computer starts up, try pressing `F12`, `F8`, `F2` or `DEL` as those are buttons that are commonly used to enter the boot menu or the BIOS.

### If you're using a Mac

Right after you press the power button to start up your computer, hold down the `Option` (a.k.a. `Alt`) key on your keyboard. A menu should pop up as the computer starts that lets you select which device you would like to boot from. Simply use the arrow keys to select the USB drive.

### If the PC/Mac instructions did not work

If none of the above works, we'll first fall back to our old friend Google and search something along the lines of "How to boot from a USB on <computer brand and computer name>". If you look around for a bit and still cannot figure out how to boot from the USB stick, then contact support@learn.co and we'll get back to you to help you out.

## Using the Linux OS

First thing you'll need to do is login. We've already created an account for you and the default password is `learnlovecode`. Once you log in, you'll want to set up SSH with Github and get you're Learn app working.

If you've never used linux before and you'd like to learn a bit more before you get started, take a look at the Welcome app. You can get to it by going to the bar at the top of the screen, selecting `System > Welcome`.

**Important Note: When you want to shutdown your bootable Linux USB go to the top menu bar and select System > Shutdown (or some other software tool), but do not use your computer's power button.**

### Get connected to GitHub

 - Type the following into your terminal: `ssh-keygen`

> Note: To use copy or paste in the terminal, use `cntrl + shift + c` and `ctrl + shift + v`

 - You will then be asked where you want to save the key: `Enter file in which to save the key (/home/flatironschool/.ssh/id_rsa):`. You can just press enter here for the default location. If there's already something there, you can overwrite it in this case.
 - Add your new SSH key to your ssh-agent by typing in `ssh-add ~/.ssh/id_rsa`.
 - Type `cat ~/.ssh/id_rsa.pub` to display your newly generated SSH key. Copy this key and [add it to your guthub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)
 - You're also going to want to let the git that is running on your machine to know you you are. You can set this up by running: `git config --global user.email "you@example.com"` and `git config --global user.name "Your Name"`.

### Set up your Learn app

 - Open the terminal (the little black box on the bar at the top of the screen) and make sure your learn gem is up to date with `gem update learn-co`.
 - Once this is done, type the command `learn whoami` to set up learn. This will ask you for the auth token at the bottom of your Learn profile. Paste it in, and you should be all set.

## Some pre-installed apps for you

These apps are by no means required tools, just a couple of things that make working a bit easier.

### Synapse

This is just a quick launcher. It has a blue S logo at the top of your screen. Right click, select preferences and you can set up a shortcut for the Activate command. This just lets you pull up a bar to quickly find and run applications.

### ScudCloud

Slack, for Linux. This is app is not currently installed, so you get to install it yourself! First, let's make sure that everything is up to date by running: `sudo apt-get update && sudo apt-get upgrade`

Next, we run the commands to install the app:

 ```
 sudo apt-add-repository -y ppa:rael-gc/scudcloud
 echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | sudo debconf-set-selections
 sudo apt-get update
 sudo apt-get install scudcloud
 ```
 And just like that, ScudCloud should be installed for you.

 >Note: `apt` is a popular package manger for linux is many apps can be installed using the `apt-get install` command.

For more information on ScudCloud, you can check out their github: https://github.com/raelgc/scudcloud

### Slack for Linux (Beta)

You can try the official beta client, but keep in mind that it is still in the works. There are binary packages for Ubuntu and Fedora that can be found here: https://slack.com/downloads

Download the 64-bit version for Ubuntu, `cd ~/Downloads` and run:
```
sudo dpkg -i slack-desktop-*.deb
```

### CompizConfig

This is an advanced settings manager for linux. I like to use this for window management myself (`ctrl + alt + RightArrow` to snap my current window to the right half of the screen or a quarter of the screen for example). If you would like to use this (and the settings I just mentioned) you will need to do the following:
 - Go to Systems > Preferences > Look & Feel > Mate Tweek
 - Select Windows on the left and then find the dropdown for Window Manger and select Compiz instead of Macro.
 - Open Compiz, use the Filter to search for 'Grid' and set your key bindings for whatever you like.

### Parcellite

This app stores your clipboard history and makes it really easy to paste anything from your history. Take a look at the settings and you can customize your keybindings for it.
