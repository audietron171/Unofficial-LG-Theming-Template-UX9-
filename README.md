# Unofficial LG Theming Template For UX9

<h4>Introduction</h4>
This is a fairly basic template for making themes for LG phones running UX9. This may work on other versions but I cannot ensure it will work. I highly condone any form of piracy and you should be very careful of only using opensource or your own pictures/icons/properties. You should be especially wary of stealing from other creators!!
<br>

I recommend having a read of this (as well as overlay theming guides including on Substratum) since it explains a little more on how the theming system works (although there appears to be a few extras in LG’s implementation, particularly around night mode resources). Just keep in mind that there are differences in how they are implemented so be careful in modifying the template (outside of what I've mentioned below):
<ul>
  <li>https://github.com/deadman96385/RRO-WIKI/wiki/About-RRO</li>
</ul>

This project also borrows a few tricks from Mark Bencze's "Samsung_Theme_Builder_Thingy_Template":
<ul>
  <li>https://github.com/markbencze/Samsung_Theme_Builder_Thingy_Template</li>
</ul>

<h4>Template structure</h4>
<ul> As described above in the RRO wiki,  the theming system uses apk's called "overlays" to replace resources in their target packages/apps. In this project, the sources for each overlay is located in the "app>individual" folder. If a resource (e.g picture, drawable, colour value etc) is in an indentical location and has the same name as in the target app, it will be replaced. Once compiled, the overlay apk's are placed in "app>src>main>assets>overlays". </ul>
</h4>

<h4>WARNING</h4>
<ul> 
  <li> Do not link resources (e.g "@color/exampleColor"). It will give an error when building but even if you add to the correct location, there is a potential to softlock your device (especially when doing to SystemUI overlays). </li>
  <li> To avoid this, use ADB when installing/uninstalling themes: </li>
    <ul>
    <li> Thanks again to Mark Bencze for this tip. As mentioned in the "Warning" section, it is possible to softlock your device when messing with SystemUI overlays. When this happens, you won't be able to uninstall your theme and safe boot will not fix it. You will need to factory reset. However, if you install/uninstall with ADB, you can uninstall the theme even when SystemUI is crashing. See here for more info: 
        https://www.dev2qa.com/android-adb-install-uninstall-app-examples/ </li> 
      <li> I highly recommend trying this at some point since ADB can be temperamental </li>
  <li> You can still transfer to you phone and install (like any regular apk) but keep in mind that there is a risk of having to format your phone to recover it.</ul> </ul>
<h4>BACKUP YOUR DEVICE FIRST!!</h4> 

<h4>Setting Up</h4>
<ul>
  <li><h5>Installing Pre-requisites:</h5>
<ol>
<li> Create a folder called "LGThemeTemplate" in a location of your choice. </li>
<li>Download the files and place in this folder. Should look like "./LGThemeTemplate/app", "./LGThemeTemplate/gradle" etc.</li>
<li>Download and install Android Studio. The latest version (tested 4.1.1) works fine. When installing, accept all defaults except you may de-select “Install Virtual Device” (themes cannot be applied to Virtual Devices since they aren’t LG).</li>
<li>Open the “LGThemeTemplate” project (will have the green Android logo) and wait for the program to complete the preparation.</li>
</ol>
<li><h5>Compiling for the first time:</h5>
<ol>
<li>By default, the project provided should compile for the first time. On the top toolbar, select “Build”>”Generate Signed Bundle/APK” and then “APK”. Click Next.</li>
<li>It should already be confirmed but confirm that in the first box, “LGThemeTemplate.app” is selected.</li>
<li>Next you will need to create a KeyStore. This will sign your APK and allow it to be installed on Android devices. Fill in the details as you see fit, you can change this later. Beware, unless you create a Google Play developer account, you will trigger Play Protect when installing your app. This isn’t an issue though, just make sure to not install using the Downloads app (I personally use LG’s File Manager). Remember your password!! </li>
<li>Create an alias.</li>
<li>On the next screen, select “Release” build variant and V2 signature versions. </li>
<li>Click Finish.</li>
<li>If you have setup this correctly, it should compile and output your app under “app\release” and be called “app-release.apk”.</li>
<li>But you’re not done yet!! If you open the overlays folder ("app\src\main\assets\overlays"), it will be empty. If you open “theme_info.json” file (one folder up), you will see the info LG uses for its themes (such as names, preview pictures and the apps it expects to see). We will generate those apps in the next step.</li>
</ol>
</li>
<li>
<h5>Compiling overlays apps</h5>
<ol>
<li>Locate the green hammer icon ("Make Project" icon on the toolbar, near the centre of the screen). Ensure the box next to it is selecting "app" (which will generate all overlays but adjust as neccessary). Click the hammer icon and wait for the Gradle Build to finsih</li>
<li>If you look back under the “overlays” folder, you will see this populated.</li>
<li>Now repeat the "Compiling for the first time" steps (you can save the passwords to make this simpler) and wait for it to finish.</li>
<li>You can now transfer this to your phone and install (keeping in mind to use an app other than Downloads or Google Files). Ignore any Play Protect warnings and up to you on submitting it to Play Protect.</li>
<li>You can now apply the theme. By default, it has no values to apply so nothing will happen. See below for how to add values/drawables </li>
 </ol>
</ul>

<h4>Adding resources to overlays</h4>
<ol>
<li>Create a folder called "res" in the same directory as the AndroidManifest.xml of the overlay you want to modify </li>
<li>Add the new resources in the same format as the ones you wish to replace (e.g. res>values>bools.xml). RRO Guides will have more detail but essentially make sure they match in name, location and preferably resolution. DO NOT LINK VALUES!! (see warning) </li>
<li>You do not create a public.xml and if you have one, you're probably stealing off someone else</li>
</ol>

<h4>Adding overlay apps</h4>
<ol>
<li>Copy one of the folders from the "app/individual" directory and place it in the same directory. Rename it to something you’ll remember (e.g. “youtube”).</li>
<li>Open Android Studio and find the “settings.gradle” file at the bottom of the Android window on the left.</li>
<li>In the include section, add the line “app:individual:name” (where name is the name of the folder in Step 1. Press “Sync” in the popup and wait.</li>
<li>Now, there should be a “build.gradle” file in the list of the other ones with the corresponding name in brackets next to it.</li>
<li>Open this file and edit the value of “applicationId” to suit the new app.</li>
<li>Now find the AndroidManifest.xml for this app (either in Android Studio or *name*/src/main). Edit the “package” name to match the name used previously and change the “targetPackage” name to match the name of the app being targeted.</li>
<li>Open the "theme_info.json" file and add another entry under "appOverlays" for your new overlay. When using this template correctly, both the "pkg" and "apk" lines will match the package name for the overlay (which you should've set in the previous step)</li>
</ol>

<h4>“Classes.dex collided” Warning</h4>
<ol>
<li>Delete all compiled “Overlay” APK’s (temporarily move if you want to keep any)</li>
<li>Delete “app-release” in release folder (or just compile again as it will clear the error)</li>
</ol>

<h4>Changing project name</h4>
<ol>
<li>Go “File”>”Project Structure” and under the “Modules” sub-menu, re-name all of the “Application ID” values to match the new name.</li>
<li>Modify the AndroidManifest.xml’s for every module (including “app”) to match the above. Follow the guide for Adding overlay apps.</li>
<li>Modify the “theme_info.json” in the main assets folder to match the new name.</li>
<li>You can also re-name the Android Studio project but this can change depending on the version so best to check online.</li>
</ol>

<h4>Changing theme preview pictures</h4>
<ol>
<li> Pictures are located in the "app>src>main>res" folder and in the drawable folders. Edit or add as needed. </li>
<li> If you add or remove any pictures, ensure the changes are reflected in the "theme_info.json" file under the "previews" section </li>
</ol>

<h4>Converting theme into an icon pack</h4>
<ol>
<li>Using the same project, open the AndroidManifest.xml for the root project ("app/source/main/AndroidManifest.xml")</li>
<li>Find the line "android:name="com.lge.theme.category" and change the value to "256" (default here is "1")</li>
<li>After installing the theme, it can now be applied under the "icons" tab</li>
</ol>

<h4>Finding Resources</h4>
This is one of the most challenging aspects of theming. However, there are ways to approach it to improve your workflow. 
<ul>
  <li>Decompile a number of system apps to help limit the resources needed to go through. For most themes, you should only need to decompile "lge-res", "LGSystemUI", "LGHome" and "LGKeyboard". Make sure you extract them from your device as different versions may work differently. </li>
  <li>Make sure you place these decompiled apps into a folder by themselves. If you have a color code for a specific item, you can just use the Windows search tool and this will look through files for it (e.g for color "#fafafa", search "#fffafafa" to find it). If you place the apps in a folder with other files (or in the root C directory) it may take a long time to find or not at all (since Windows cannot often index all files). </li>
</ul>

<h4>Quick Settings icons</h4>
I highly recommend not modifying these until you have worked on theming for a while since this can be very time consuming
<ul> 
<li>Icons are drawn using Android Vector files. These are generated by Android Studio when importing supported vector files so there can be compatibility issues, make sure you read errors (if given). </li>
<li> Recommended procedure is to generate SVG files using a program like Inkscape. To ensure that the image is drawn at a size matching existing icons, make sure you configure the canvas size to be 27x27px and the viewport size as 108x108px. These values are important if you are using the existing QS icon dimensions. </li>
</ul>



