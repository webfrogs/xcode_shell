Introduce
===========
----

This repository contains a series of useful shell scripts which can help you to work effectively when programming for iOS platform.


Necessary
===========

-----
To use scripts of this repository, you should install the "Command Line Tools" in the setting of xcode first.


Detail
===========

----

####1.compile and package xcode project

You can do this by using "ipa-build" shell script.

**ipa-build**:This script is created to compile the xcode project and package the project to an ipa file.

Usage: 

	ipa-build <project directory> [-c <project configuration>] [-o <ipa output directory>] [-n]

Options:

	-c NAME		the configuration of project used to compile.Default is Release
	-o PATH		output path for ipa file(must be a directory)
	-n			clean the project before compling
	
If script executed successfully,an ipa file is created in the path: <project path>/build/ipa-build.


####2.publish project

**ipa-publish**: I will write it later.


####3.add @2x suffix to image files

When programming for retina device of iOS,the image file you used should add the suffix of @2x. Using the script "add2x" can help you do this automaticly.

**add2x**: add suffix of @2x to all the image files(just png and jpg file) .This script work in the current directory.

Usage:    
1. go to the directory which contains images should be added suffix.    
2. execute the add2x script.

**note**: There is a bug of this script.If your image file name contains blank spaces, script can not work correctly.




