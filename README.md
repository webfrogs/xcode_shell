Introduce
===========
----

This repository contains a series of useful shell scripts which can help you to work effectively when programming for iOS platform.
####Include:
* build .ipa package
* publish .ipa file to fir.im or your own server
* send email



Necessary
===========

-----

* Mac OS X
* "Command Line Tools" of xcode
* ruby with "json" package installed



Detail
===========

----

##1.compile and package xcode project or workspace

You can do this by using "ipa-build" shell script.

This ipa-build script is created to compile the xcode project and package the project to an ipa file.

####Usage: 

***building xcode project***

	ipa-build <project directory> [-c <project configuration>] [-o <ipa output directory>] [-t <target name>] [-n]

***building xcode workspace***

	ipa-build  <workspace directory> -w -s <schemeName> [-c <project configuration>] [-n]

####Options:

	-c NAME		the configuration of project used to compile.Default is Release
	-o PATH		output path for ipa file(must be a directory)
	-t NAME		the target which should be compiled
	-w			build xcode workspace	
	-s NAME		the schemal to be used for compiling
	-n			clean the project before compling
	
####Example:

***build project***
    
If you have an iOS project in the path ~/iphone, and the ipa-build script is put in the path ~/xcode-shell.You want to build this project with 'Release' configuration.Just using script like this:

	cd ~/iphone
	~/xcode-shell/ipa-build .

If you want to assign specific configuration or target, you can add relevant options to the command.

***build workspace***

If ~/iphone is a xcode workspace and the scheme used for compile named 'test'.The ipa-build script is put in the path ~/xcode-shell.Using script like this:

	cd ~/iphone
	~/xcode-shell/ipa-build . -w -s test

You can also assign a specific configuration by using -c option.

	
	Note:If script executed successfully,an ipa file is created in the path: <project path>/build/ipa-build.

##2.compile project used CocoaPods

[CocoaPods](https://github.com/CocoaPods/CocoaPods) is an Objective-C library manager.If you use it in your iOS project.You can also use 'ipa-build' script to build by assign workspace and scheme, or you can use the 'cocoapods-build' to build it more easily.

####Usage:

	cocoapods-build <cococapods project path> [<build configuration>] 

####Example:

	cd ~/iphone
	~/xcode-shell/cocoapods-build . Debug


##3.publish project

###ipa-publish
####Configure
You must configure the script before using at the first time. Open it in any text editor and input you own configurations. Such as ftp address, app download url, email sender and email receiver. After that you can run this script to publish app to your own server.
Note that installing app from your own server should respect the protocol named "itms-services". To learn more about "itms-services" you can click blog [Wireless AdHoc Distribution](http://gknops.github.io/adHocGenerate/)(English) or blog [ios实现itms-services协议企业内发布或者越狱发布](http://blog.csdn.net/wyq5119275/article/details/16946009)(中文).

####Usage:

	ipa-publish <project root path> [y <should send notification email>]

####Examples:

    ~/xcode-shell/ipa-publish . y   #publish and send email
    ~/xcode-shell/ipa-publish .     #just publish


###ipa-publish-fir
This script is similar to "ipa-publish". Both of them are using to publish app to somewhere. But this script will publish app to [fir.im](http://fir.im). So it is more easier to use, as you don't need a special server and FTP. You can use it without any configration, unless you want to send email to notify somebody.

####Configure
If you want to send email to notify somebody. Open the script, and changed the value of "email_reciver". This field may contain one or more than one emails.


####Usage:

	ipa-publish-fir [-d directory>] [-e] [-l number] [-m message]

####Options:

	-d path		the root directory of project
	-e			send email after publishing
	-l number	limit of git log, which will be used as change log.
	-m message	used as chang log


####Examples:

    ~/xcode-shell/ipa-publish-fir -d . -el20 -m "haha"	#Publish and send email. The change log on fir and in email will be "haha"+<last 20 logs of git>
    ~/xcode-shell/ipa-publish-fir -d .     			#just publish


##4.add @2x suffix to image files

When programming for retina device of iOS,the image file you used should add the suffix of @2x. Using the script "add2x" can help you do this automaticly.

**add2x**: add suffix of @2x to all the image files(just png and jpg file) .This script work in the current directory.

Usage:    
1. go to the directory which contains images should be added suffix.    
2. execute the add2x script.

**note**: There is a bug of this script.If your image file name contains blank spaces, script can not work correctly.




