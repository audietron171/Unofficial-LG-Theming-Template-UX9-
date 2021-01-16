# Unofficial-LG-Theming-Template-UX9-

<h4>Introduction</h4>
This is a fairly basic template for making themes for LG phones. I highly condone any form of piracy and you should be very careful of only using opensource or your own pictures/icons/properties. You should be especially wary of stealing from other creators!! 
I recommend having a read of this since this explains a little more on how the theming system works (although there appears to be a few extras in LG’s implementation, particularly around night mode resources):
-	https://github.com/deadman96385/RRO-WIKI/wiki/About-RRO

<h4>Setting Up</h4>
	Installing Pre-requisites:
1.	Download the .zip file called “LGThemesTemplate.zip” and extract to a location of your choice.
2.	Download and install Android Studio. The latest version (tested 4.1.1) works fine. When installing, accept all defaults except you may de-select “Install Virtual Device” (themes cannot be applied to Virtual Devices since they aren’t LG).
3.	Open the “LGThemesTemplate” project (will have the green Android logo) and wait for the program to complete the preparation.
Compiling for the first time:
1.	By default, the project provided should compile for the first time. On the top menu, select “Build”>”Generate Signed Bundle/APK” and then “APK”. Click Next.
2.	It should already be confirmed but confirm that in the first box, “LGThemeTemplate.app” is selected.
3.	Next you will need to create a KeyStore. This will sign your APK and allow it to be installed on Android devices. Fill in the details as you see fit, you can change this later. Beware, unless you create a Google Play developer account, you will trigger Play Protect when installing your app. This isn’t an issue though, just make sure to not install using the Downloads app (I personally use LG’s File Manager). Remember your password!!
4.	Create an alias.
5.	On the next screen, select “Release” build variant and V2 signature versions. I’m not 100% sure on what this does but it works 😊.
6.	Click Finish.
7.	If you have setup this correctly, it should compile and output your app under “app\release” and be called “app-release.apk”.
8.	But you’re not done yet!! On the left hand screen (in the top left), select Project and in the menu, select Android. If you’re already on this screen, great!
9.	Under “Assets”>”Overlays”, you will notice that there are no apps. If you open “theme_info.json” you will see the info LG uses for its themes (such as names, preview pictures and the apps it expects to see). We will generate those apps in the next step.

<h4>Actually making a Theme</h4>
1.	Locate the “Make Project” button on the top-middle of the screen (just under the project name), confirm that “app” is selected and press the green hammer icon.
2.	This will generate those apps that the theme will apply. If you look back under the “overlays” folder, you will see this populated. 
3.	Now repeat the Compiling for the first time steps (you can save the passwords to make this simpler and wait).
4.	You can now transfer this to your phone (via OneDrive, Google Drive, Bluetooth etc) and install (keeping in mind to use an app other than Downloads or Google Files). Ignore any Play Protect warnings and up to you on submitting it to Play Protect.
5.	You can now apply the theme.
6.	I recommend to always restart your device to ensure themes are applied correctly but there’s a quicker way. Turn night mode on & off and force stop Home. 
7.	I’ve always had issues with themes being “updated” so I also recommend to always uninstall your theme before installing a new version.
8.	You can add resources to each of these overlay apps by placing them in the corresponding app folder in “app\individual” and using the same setup as in the original app.

<h4>Adding overlay apps</h4>
1.	Copy one of the folders from above and place it in the same directory. Rename it to something you’ll remember (e.g. “telegram”).
2.	Open Android Studio and find the “settings.gradle” file at the bottom of the Android window on the left.
3.	In the include section, add the line “app:individual:name” (where name is the name of the folder in Step 1. Press “Sync” in the popup and wait.
4.	Now, there should be a “build.gradle” file in the list of the other ones with the corresponding name in brackets next to it.
5.	Open this file and edit the value of “applicationId” to suit the new app. 
6.	Now find the AndroidManifest.xml for this app (either in Android Studio or name/src/main). Edit the “package” name to match the name used previously and change the “targetPackage” name to match the name of the app being targeted. 

<h4>Changing project name</h4>
1.	Go “File”>”Project Structure” and under the “Modules” sub-menu, re-name all of the “Application ID” values to match the new name.
2.	Modify the AndroidManifest.xml’s for every module (including “app”) to match the above. Follow the guide for Adding overlay apps. 
3.	Modify the “theme_info.json” in the main assets folder to match the new name.
4.	You can also re-name the Android Studio project but this can change depending on the version so best to check online.

<h4>“Classes.dex collided” Warning</h4>
1.	Delete all compiled “Overlay” APK’s (temporarily move if you want to keep any)
2.	Delete “app-release” in release folder (or just compile twice)





