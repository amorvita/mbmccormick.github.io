--- 
layout: post
title: Getting Serious About Windows Phone 7 Development
excerpt:
  Today I'd like to talk, and perhaps rant, about Windows Phone development. I've just published my third Windows Phone application to the Marketplace and I have four other apps that I'm working on. I've been doing this for about 6 months now and I've picked up a few things along the way that I'd like to share.
---
Today I'd like to talk, and perhaps rant, about Windows Phone development. I've just published my third Windows Phone application to the Marketplace and I have four other apps that I'm working on. I've been doing this for about 6 months now and I've picked up a few things along the way that I'd like to share. These tips, suggestions, and best practices should be used by every developer to ensure that the apps they create are seamless extensions of the beautiful Windows Phone operating system.

## Use the Silverlight Toolkit for Windows Phone in every application
Use this toolkit in every application that you develop. Windows Phone has a beautiful interface and the applications should be no different. The <a href="http://silverlight.codeplex.com/" target="_blank">Silverlight Toolkit for Windows Phone</a> has a lot of controls that the default Windows Phone libraries don't have. Download and install the <a href="http://silverlight.codeplex.com/releases" target="_blank">latest releaase</a> of the toolkit and add the following line to your page header to get started:

```
xmlns:toolkit="clr-namespace:Microsoft.Phone.Controls;assembly=Microsoft.Phone.Controls.Toolkit"
```

Another important component of the Silverlight Toolkit is the transitions. Your application should use the <a href="http://worldwidecode.wordpress.com/2011/08/05/page-transitions-in-windows-phone-7-part-2/" target="_blank">turnstyle transition</a> on every page. You're making a Windows Phone application, not a website. The Metro interface is about motion, and your app needs to use this transition to make it look like a Metro application. Just copy and paste this into your pages:
  
<script src="https://gist.github.com/1396098.js"> </script>
  
Enable the <a href="http://msdn.microsoft.com/en-us/library/ff941094(v=vs.92).aspx" target="_blank">Tilt Effect</a> to give your users some tactile feedback on buttons and text. Let them know that whatever they just tapped on is about to do something. This effect is used throughout the phone and your app should be no different. The Silverlight Toolkit makes it easy to do this, just copy and paste `toolkit:TiltEffect.IsTiltEnabled="True"` in your page headers and you're good to go.

## Use the Progress Indicator, and put it in the System Tray
If your application does any sort of background work or requires some loading time, show a <a href="http://msdn.microsoft.com/en-us/library/microsoft.phone.shell.progressindicator(v=vs.92).aspx" target="_blank">Progress Indicator</a>. This will let the user know that your application is working and isn't broken. The Progress Indicator control is the same one you see throughout the operating system. And unless your application is going to apply some sort of overlay on top of the application while it is loading, put your Progress Indicator in the <a href="http://msdn.microsoft.com/en-us/library/microsoft.phone.shell.systemtray(v=vs.92).aspx" target="_blank">System Tray</a>. Centering the Progress Indicator vertically in combination with a semi-transparent overlay is fine, but if you're not going to do that, make use of the System Tray's Progress Indicator property like this:

<script src="https://gist.github.com/1396105.js"> </script>

Make sure you do this only after the page has finished loading, in the `PhoneApplicationPage_Loaded` event. Otherwise you won't be able to access the `SystemTray` classes.

## Use the Phone Accent Brush where appropriate
Windows Phone is about simplicity, and the simple Metro interface is what makes it beautiful. Users have the ability of choosing a theme and an accent color. All of the other applications on the phone make use of this accent color in some way and yours should be no different. Use your best judgement on how best to integrate this, obviously you don't want to overwhelm your user with the accent color.

You can access this property in your XAML with `{StaticResource PhoneAccentBrush}` or in your code with `(SolidColorBrush)Resources["PhoneAccentBrush"]`.

## Take better screenshots
If you have a Windows Phone device to use during application testing, download and install <a href="http://forum.xda-developers.com/showthread.php?t=1316199" target="_blank">Screen Capturer</a> to your developer unlocked device. This app allows you to take screenshots on your phone using the camera button from inside of your application. The tool saves your screenshots to your Saved Pictures album and you can sync these to your computer with Zune. This tool will ensure that you're getting quality screenshots at the exact <a href="http://msdn.microsoft.com/en-us/library/hh184844(v=vs.92).aspx" target="_blank">resolution needed for the Marketplace</a>.

If you don't have a Windows Phone device to test your application on, you'll need to use some sort of screen capture tool to grab screenshots of the emulator. When you do that, disable the <a href="http://msdn.microsoft.com/en-us/library/gg588380(v=vs.92).aspx" target="_blank">Frame Rate Counter</a> in the emulator. Unless you plan to show that Counter in your application, it shouldn't be in your screenshots. Comment out this line in your `App.xaml.cs` file to disable the Frame Rate Counter:

```
Application.Current.Host.Settings.EnableFrameRateCounter = true;
```

## Integrate with the phone
If you're writing an app that could make use of another built-in function of the phone, then integrate it! Make use of the built-in Navigation services, take pictures with the phone's Camera application, allow phone numbers to be called with the Dialer, allow the user to save contact information to their Contacts, open links in the Web Browser. There's a ton of opportunities to integrate with the phone and this integration will provide a more native experience for your users.

<a href="http://msdn.microsoft.com/en-us/library/microsoft.phone.tasks(v=vs.92).aspx" target="_blank">Complete list of Launchers and Choosers</a>

## Release often, but not early
Getting your application certified and published on the Windows Phone Marketplace takes an average of 3 days. If your publishing on a weekend, expect a 4 to 5 day turnaround time. Microsoft has real people testing your application on real phones, and that takes a while. So make sure that you test your application thoroughly before you submit it to the Marketplace. If you discover a bug right after you submit your application for certification, it will be about a week before your users will see a fix. Not only do you have to wait for the 3 day certification process of your fix, you can't resubmit your application until your initial submission has been tested in full.

<a href="http://msdn.microsoft.com/en-us/library/hh202928(v=vs.92).aspx" target="_blank">Windows Phone Marketplace certification process</a>

## Create attractive icons and splash screens
This is perhaps my biggest pet peve about Windows Phone applications in the Marketplace today: their icons and splash screens are just awful. When I install your application, it becomes a part of the user interface. Every time I open my Start Menu, I'm going to see your application icon. If it's ugly or if it doesn't fit with the Metro interface, I'm uninstalling your application. Your application could be awesome and do great things, but if the icon sucks I'm not using your application.

The same thing applies for splashs creens. Make it look pretty or don't use it at all. Nothing says that your application needs a splash screen, so either make something beautiful and use it or just don't have one.

<a href="http://expression.microsoft.com/en-us/gg317447" target="_blank">Creating Windows Phone 7 Application and Marketplace icons</a>

## Follow these best practices
Lastly, follow these best practices published by Microsoft about Windows Phone interface design. This guide talks about text placement, proper margins, color palettes, icon design, keyboard types, screen orientations, and much more. Chances are if you have a question about user interface best practices for Windows Phone applications, you will find it here.

<a href="http://blogs.msdn.com/b/silverlight_sdk/archive/2011/01/07/windows-phone-7-design-guidelines-cheat-sheet.aspx" target="_blank">Windows Phone 7 Design Guidelines cheat sheet</a>