# rConfig 3.8beta readme

### Introduction
The rConfig community has been asking for a long time for multi-vendor support. It's here. I've created a template based connection feature that allows you to specify different 
vendors connection profiles, easily. From upper and lower case username prompts, to connections timeouts, paging commands and so on... you can now get very granular on how you connect 
to various vendors network devices, Linux servers and other SSH/ Telnet based devices from rConfig. 

The other major feature in this beta release is encrypted device passwords. Using a simple key and Initialization vector, stored securely, all of your precious network credentials
will be stored in the database in a highly encrypted manner and decrypted just before rConfig connects to your devices. 

### About the beta
Its very important that I release a very stable version of rConfig with these key features. That said, I need two things from beta contributors; 
* Expect some broken things, but be very specific when your reporting errors. Be prepared to be part of the solution and resolution.
* Stay engaged i.e. install new fixes when they are released, be prepared to re-install a few times, run and re-run upgrades from 3.7.5 etc.. and then feedback

If you can do this, you'll play a key part in making the new release very successfully. On that last point, right now I've dubbed this beta release 3.8beta. It may well be the case
that when eventually ready to release, I may move this to a full blown V4. But remains to be seen. 

### Getting started with the beta
First things first... __Do not install the beta for production use, and DO NOT upgrade your existing installation of rConfig with this beta version__. Be patient!!!

#### Installation
The beta installation is going to be very similar to how you would install rConfig today - with a twist.
1. Visit https://www.rconfig.com/rconfig-support/guides/61-rconfig-3-5-installation-guide and complete a v3.5 installation per the instructions. but do not run the rConfig web based installer
2. Run the following commands to download and install rConfig 3.8beta
```
    curl -O http://www.rconfig.com/downloads/rconfig-3.8.0-beta.zip -A "Mozilla"
    mv rconfig rconfig.3.7.5.bak
    unzip rconfig-3.8.0-beta.zip
    mkdir rconfig/tmp
    chown -R apache /home/rconfig
```
Open https://YourHostOrIpAddress/install/ and begin the installation process.

Upgrades will be identical to existing process. Except you cannot download the file from the rconfig.com until I post it, and will notify its exact URL on the private slack channel.

You need to manually set your keys for password encryption in the config/config.inc.php file. If you do not set a key, the passwords for new devices will be saved in plan text in the DB

#### Build Notes
Please review 3.8updates.md in the root directory of rConfig3.8 beta or on the 3.8dev branch in github... I was using this as a running task list for the duration of the beta build. Any items prefixed with a dash '-' are completed items.
I will now move over to the github issues board to log and track issues for the beta duration - slack integration with github is in place and you should get notifications of
commits, issues etc... realtime!


#### Testing
I've fixed and updated quite a bit in this beta release. But the two main items to be tested are;
* Templates for device connections
* Device Password encryption

Generally, most other functionality of rConfig should work the same, such as adding devices, creating schedules and so on. You should create your own test plan based on your 
every day use of rConfig and feedback positive or negative results. 

##### Device Templates
I hope this is pretty self explanatory. But to get you started here are some pointers;
1. Go to 'Devices' Menu and 'Connection Templates' menu. You will see four default templates for Cisco based devices. Study these templates. Know their names. 
2. Head over and add a new device. Choose the device template you need to use for the connection to the device. Such as SSH with enable mode etc...
3. Create a new schedule to download the devices config commands (manual downloads not work for 3.8.0 beta launch)
4. Go to this KB article and follow it to invoke a manual download using the schedule ID you just created
5. Test and repeat. Feedback to slack channel. 

I suggest starting with Cisco devices, or devices you were already using in 3.7.5 before creating new templates and experimenting. 

I've created a new repo to store community created templates for devices. When you get working templates for new devices and vendors please submit here https://github.com/rconfig/rConfig-templates
Currently, we have HP, Fortinet, Dell and Cisco templates tested and working in the repo. The Beta, will only ship with Cisco templates, you need to add others yourself manually.

##### Password Encryption
I have updated the Password encryption function from previous beta releases. You can now implement Password encryption through the settings page. Please read and follow the instructions
carefully. Once you have enabled PW encryption, check the DB for encrypted passwords, and check again as you add and edit devices. Please also verify it is working by carrying out test downloads
on devices.

#### Feedback and bugs
Slack by invite, github issues board for 3.8dev tags only

#### URLs
rConfig 3.8 Beta Repo - https://github.com/rconfig/rconfig/tree/3.8dev
Github Issues board - https://github.com/rconfig/rconfig/issues
rConfig Device Templates Repo - https://github.com/rconfig/rConfig-templates


