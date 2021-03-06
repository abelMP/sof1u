# ScrollOutF1 Updated #

This is a slightly modified version of the ScrollOutF1 email gateway software.

## Why? ##

Because we can _(the software is licensed under GPL version 2)_ and because the software is very good, but unfortunately it lacks support for modern Operating Systems like Debian 9.x and Ubuntu 16.04 LTS, basically for these two reasons:

* In Debian 9.x it insist on using PHP ver 5.x and the mainstream version is now 7.x
* In Ubuntu 16.04 LTS the PHP scripting language version 5.x was deprecated an removed from the repositories and is no longer an option.

I tried (unsuccessfully) to contact the developer to help him build a fix with our tests, but since there was some real interest in our country (Cuba) for using this solution, but based on modern versions of Debian / Ubuntu, I put hands to work and this is the result.

The changes made to the software were only the required to make it run on moder Ubuntu (Xenial 16.04 LTS) and Debian (Stretch 9.x) systems with up to date PHP versions (7.0) and some other tricks for the install and setup process.

## Warning! ##

For the moment there is no way to update of it from the developer site, as it will break the fix I have introduced. I will try to reach Marius Gologan (the main developer) to merge this solution into his official code tree.

If you try to run the update.sh script you will get a warning like this one.

As I don't provide any functional update mechanism by now (other than a reinstall) I will make a notice in the Changelog section about the details when the a fix is released; so RTFM.

### Changelog: ###

* 27 nov 2017 (1): Repository creation based on the actual tar file from www.scrolloutf1.com page
* 27 nov 2017 (2): Basic support for Ubuntu 16.04 LTS, in fact it's tweaked to **ONLY** work on that system at this point, it will not work on older ones (either Ubuntu or Debian) I will soon introduce more validations on the script to make it support new and old versions.
* 27 nov 2017 (3): The validation for newer Ubuntu and Debian is in place, it will detect the version and install the corresponding software and config files; also it will now work for older versions like the official scrolloutf1.tar file does. _(Linus Torvals style: don't break it trying to fix it)_
* 1 dec 2017: Fix for clamav-amavisd integration, if you installed this software before December 1st 2017, you may want to look at [Issue #2](https://github.com/pavelmc/sof1u/issues/2) for an easy fix.
* 11 dec 2017: Fix for Debian 9, the nginx server won't start because there was a cert missing: there was a problem with the cert generation under certain circumstances, fixed that and set some validations on the conditions of the failure to warn the user about.

## Roadmap / TODO ##

* Reach the main developer to try to merge the fix with the official code.
* Patchs for minor bugs.

## Installation ##

_**Note:** If you are using an Ubuntu container in a Proxmox Virtualization Environment please remove postfix before beginning installation, with:_

```
apt-get remove --purge postfix* -y
```

* You need a **fresh** install of Debian 7/8/9 or Ubuntu 14.04/16.04 LTS versions, otherwise it will fail. (Did you see the bold _**fresh**_ word?)
* Please check you have set up your server IPs, hostname and DNS domain correctly, once you start installing those values will be hard-coded in a few places.
* Assuming the FQDN of your server is _"egw.mydomain.com"_, you can check if your hostname & domain settings are correct by running these two commands on console:

```
user@server:~/$ hostname
egw
user@server:~/$ hostname -f
egw.mydomain.com

```

* Please check your repository configurations and fully update your system before continuing.
* Download the software:

Here you have two options: if the PC has internet connection just do this in console:

```
cd /tmp
wget https://github.com/pavelmc/sof1u/archive/master.zip -O sof1u-master.zip
```

If you don't have internet on the target PC, you can download it to your desktop by just clicking the the green button on the top-right part of this page and select "Download ZIP", once you has the file, copy it to the target PC into the /tmp folder (use your prefered method here); note that the name of the file must be _"sof1u-master.zip"_.

* Extract it with:

```
unzip sof1u-master.zip
```

* Extract the scrollOut F1 folder from the created one with:

```
mv sof1u-master/* ./
```

* Change the permissions of the files with:

```
chmod 755 /tmp/scrolloutf1/www/bin/*
```

* Invoke the install script with:

```
/tmp/scrolloutf1/www/bin/install.sh
```

* Follow the instructions and that's all.


## Author ##

I'm Pavel Milanes, a FLOSS enthusiast and SysAdmin by choice, I live in Cuba where a masive migration to FLOSS is taking place system by system, all that by dedicated sysadmins who spend precious hours of their time to make things work and work fine.

This is a small contribution for them, you can reach me by email or [telegram](https://t.me/sysadmincuba), also we have place on the net: [SysAdminsdeCuba](https://www.sysadminsdecuba.com)

### Want to say thanks? ###

If this mod work for you, please, let me know.

If you like to make a donation, contact me by mail for instructions, sadly PayPal does not work with Cuba.

If it does not work for you: tell us too! We will try to figure out what's going wrong and fix it. Please use the Issues tab on top of this page for that.

Cheers.
