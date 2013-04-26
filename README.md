Introduce
===========
----

This repository contains a series of useful shell scripts which can help you to work effectively when programming for iOS platform.


Necessary
===========

-----

* Mac OS X
* "Command Line Tools" of xcode



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

**ipa-publish**: I will write it later.


##4.add @2x suffix to image files

When programming for retina device of iOS,the image file you used should add the suffix of @2x. Using the script "add2x" can help you do this automaticly.

**add2x**: add suffix of @2x to all the image files(just png and jpg file) .This script work in the current directory.

Usage:    
1. go to the directory which contains images should be added suffix.    
2. execute the add2x script.

**note**: There is a bug of this script.If your image file name contains blank spaces, script can not work correctly.




