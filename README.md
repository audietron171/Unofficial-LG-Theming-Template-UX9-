# Unofficial LG Theming Template For UX9

<h4>Introduction</h4>
This is a fairly basic template for making themes for LG phones running UX9. This may work on other versions but I cannot ensure it will work. I highly condone any form of piracy and you should be very careful of only using opensource or your own pictures/icons/properties. You should be especially wary of stealing from other creators!! I recommend having a read of this since this explains a little more on how the theming system works (although there appears to be a few extras in LG’s implementation, particularly around night mode resources):
<ul>
  <li>https://github.com/deadman96385/RRO-WIKI/wiki/About-RRO</li>
</ul>

<h4>Setting Up</h4>
<ul>
  <li><h5>Installing Pre-requisites:</h5>
<ol>
<li> Create a folder called "LGThemeTemplate" in a location of your choice. </li>
<li>Download the files and place in this folder. Should look like "./LGThemeTemplate/app", "./LGThemeTemplate/gradle" etc.</li>
<li>Download and install Android Studio. The latest version (tested 4.1.1) works fine. When installing, accept all defaults except you may de-select “Install Virtual Device” (themes cannot be applied to Virtual Devices since they aren’t LG).</li>
<li>Open the “LGThemeTemplate” project (will have the green Android logo) and wait for the program to complete the preparation.</li>
</ol>
<h5>Compiling for the first time:</h5>
<ol>
<li>By default, the project provided should compile for the first time. On the top menu, select “Build”>”Generate Signed Bundle/APK” and then “APK”. Click Next.</li>
<li>It should already be confirmed but confirm that in the first box, “LGThemeTemplate.app” is selected.</li>
<li>Next you will need to create a KeyStore. This will sign your APK and allow it to be installed on Android devices. Fill in the details as you see fit, you can change this later. Beware, unless you create a Google Play developer account, you will trigger Play Protect when installing your app. This isn’t an issue though, just make sure to not install using the Downloads app (I personally use LG’s File Manager). Remember your password!! </li>
<li>Create an alias.</li>
<li>On the next screen, select “Release” build variant and V2 signature versions. </li>
<li>Click Finish.</li>
<li>If you have setup this correctly, it should compile and output your app under “app\release” and be called “app-release.apk”.</li>
<li>But you’re not done yet!! On the left hand screen (in the top left), select Project and in the menu, select Android. Disregard if already on this view</li>
<li>Under “Assets”>”Overlays”, you will notice that there are no apps. If you open “theme_info.json” you will see the info LG uses for its themes (such as names, preview pictures and the apps it expects to see). We will generate those apps in the next step.</li>
</ol>
  </li>
<li>
<h5>Actually making a Theme</h5>
<ol>
<li>Locate the “Make Project” button on the top-middle of the screen (just under the project name), confirm that “app” is selected and press the green hammer icon.</li>
<li>This will generate those apps that the theme will apply. If you look back under the “overlays” folder, you will see this populated.</li>
<li>Now repeat the Compiling for the first time steps (you can save the passwords to make this simpler and wait).</li>
<li>You can now transfer this to your phone (via OneDrive, Google Drive, Bluetooth etc) and install (keeping in mind to use an app other than Downloads or Google Files). Ignore any Play Protect warnings and up to you on submitting it to Play Protect.</li>
<li>You can now apply the theme.</li>
<li>I recommend to always restart your device to ensure themes are applied correctly but there’s a quicker way. Turn night mode on & off and force stop Home.</li> 
 </ol>
</ul>

<h4>Adding overlay apps</h4>
<ol>
<li>Copy one of the folders from above and place it in the same directory. Rename it to something you’ll remember (e.g. “youtube”).</li>
<li>Open Android Studio and find the “settings.gradle” file at the bottom of the Android window on the left.</li>
<li>In the include section, add the line “app:individual:name” (where name is the name of the folder in Step 1. Press “Sync” in the popup and wait.</li>
<li>Now, there should be a “build.gradle” file in the list of the other ones with the corresponding name in brackets next to it.</li>
<li>Open this file and edit the value of “applicationId” to suit the new app.</li>
<li>Now find the AndroidManifest.xml for this app (either in Android Studio or name/src/main). Edit the “package” name to match the name used previously and change the “targetPackage” name to match the name of the app being targeted.</li>
<li>You can add resources to each of these overlay apps by placing the new resources in a similar format to the original (e.g. "app\individual\common\src\main\res")
</ol>

<h4>Changing project name</h4>
<ol>
<li>Go “File”>”Project Structure” and under the “Modules” sub-menu, re-name all of the “Application ID” values to match the new name.</li>
<li>Modify the AndroidManifest.xml’s for every module (including “app”) to match the above. Follow the guide for Adding overlay apps.</li>
<li>Modify the “theme_info.json” in the main assets folder to match the new name.</li>
<li>You can also re-name the Android Studio project but this can change depending on the version so best to check online.</li>
</ol>

<h4>“Classes.dex collided” Warning</h4>
<ol>
<li>Delete all compiled “Overlay” APK’s (temporarily move if you want to keep any)</li>
<li>Delete “app-release” in release folder (or just compile again as it will clear the error)</li>





