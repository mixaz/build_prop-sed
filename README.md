Script to update properties files via recovery.

Current code enables ADB in /system/build.prop.

The code taken from: https://forum.xda-developers.com/showpost.php?p=19093919&postcount=20

=====================================

FIRST: The location of shell in recovery should be /sbin/sh. But when you are booted into the ROM it will be /system/bin/sh. Recovery and the ROM are 2 seperate partitions and setup.

SECOND: The script linked WILL NOT add the lines you want if it doesn't exist in the build.prop to begin with. 

I removed some things from this as it was used for something else. I haven't tested it but all I did was remove some extra things that were in it and renamed some things.


First thing to note is that in the updater-script you need to extract the files. We will get to that in a second. There are 2 files that are used. Create a folder inside the zip called tmp. Inside the tmp folder should be 2 files. The first one is called mytweaks.sh and the second one is called update-build.prop.

There should be no reason to mess with mytweaks.sh unless "#!/sbin/sh" needs to be changed. 

Inside the update-build.prop file you can delete what I have posted and add the lines you want to add or modify in the build.prop. Make sure that each setting is on it's own line. 

The script should run through each line and if it found a line that has the same text before the "=" it will remove that line and then add the contents of update-build.prop to the bottom of the build.prop file. This way, even if the line is not present in the build.prop it will still be added. 



