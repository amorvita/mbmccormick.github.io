---
layout: post
title: Install Windows 8 on a Google Cr-48
date: 2011-09-14 00:00
comments: true
categories: []
---
<p>Clearly <a href="http://mbmccormick.com/2011/08/install-ubuntu-11-04-on-a-google-cr-48/" target="_blank">I'm trying</a> to find a good use for my <a href="http://www.google.com/chromebook/" target="_blank">Google Cr-48</a>. Today I was able to get the <a href="http://www.microsoft.com/presspass/press/2011/sep11/09-13FutureofComputingPR.mspx" target="_blank">Windows 8 Developer Preview</a> installed on a Google Cr-48. It is somewhat involved, but nonetheless I will detail my steps here. This is not for the faint of heart, and I take no responsibility for what you do to your laptop. This guide assumes that you have backed up any important information from your existing OS on your Google Cr-48, whether that is Chrome OS, Ubuntu, or something else. The instructions below will completely erase the data on your laptop and overwrite with Windows 8.</p>

<p><strong>Disable BIOS protection:</strong></p>

<ol>
    <li>To do this, you will need to crack open the shell of your Google Cr-48.</li>
    <li>Flip your laptop over and remove the battery.</li>
    <li>If you have not already done so, now is a good time to flip the switch to enable <a href="http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information" target="_blank">developer mode</a>.</li>
    <li>Remove the two rubber feet on the underside of the laptop using a knife or flat-head screwdriver.</li>
    <li>Remove the two screws underneath the two rubber feet.</li>
    <li>Next, remove all of the remaining screws that you can see.</li>
    <li>Once you have removed all of the screws, carefully pry off the bottom case. Start at the back under the screen hinge and work your way around the laptop, moving to the VGA port first and ending with the USB and headphone ports.</li>
</ol>


<p><strong>Flash the InsydeH2O BIOS:</strong></p>

<div>
<ol>
    <li>With the case still removed and your device in developer mode, turn on your Google Cr-48.</li>
    <li>At the unhappy Chrome face screen, press CTRL + D to bypass the warning.</li>
    <li>Let Chrome erase the stateful partition and, at the setup screen, select a wireless network and agree to the terms of service. Stop when you get to the login screen.</li>
    <li>Press CTRL + ALT + => (where => is where the F2 key would be) to launch a shell.</li>
    <li>Login as the user chronos, no password is needed.</li>
    <li>Elevate your permissions to root with sudo su.</li>
    <li>Next, download the <a href="http://www.insydesw.com/solutions/pc/insydeh2o.cfm" target="_blank">InsydeH2O BIOS</a> with wget http://mbmc.co/oAGPNk.</li>
    <li>Extract the archive with tar -xvzf oAGPNk.</li>
    <li>Flash the BIOS with flashrom -w cr48.bin, ignoring any error output.</li>
    <li>Restart the computer to boot to the new BIOS, removing your installation media.</li>
</ol>
<strong>Install Windows 8:</strong>
<div>
<ol>
    <li>Create a <a href="http://www.ghacks.net/2011/09/14/how-to-install-windows-8-from-usb-key/" target="_blank">bootable USB drive with Windows 8 Developer Preview installed</a>.</li>
    <li>Insert the drive to your laptop and power it on.</li>
    <li>The laptop should automatically detect your USB drive and boot to it.</li>
    <li>Follow the on-screen instructions to begin setup.</li>
    <li>When prompted, select the Custom Installation option and NOT the Upgrade option.</li>
    <li>When prompted, delete all of the existing partitions until one Unallocated Space item exists in the list of partitions. Select this partition as the installation destination.</li>
    <li>At this point, you should allow the installer to finish and reboot your computer. Follow the on-screen guide to complete the installation.</li>
</ol>
</div>
<strong>Install Hardware Drivers:</strong>
<div>
<ol>
    <li>Install the following hardware drivers in order.</li>
    <li>Increase SSD I/O performance with <a href="http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2101&lang=eng&FamilyId=40" target="_blank">Intel Rapid Storage Technology</a>.</li>
    <li>Update the chipset firmware with <a href="http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Chipsets&ProductLine=Chipset+Software&ProductProduct=Intel%C2%AE+Chipset+Software+Installation+Utility&ProdId=816&LineId=1090&FamilyId=40" target="_blank">Intel Chipset Installation Utility</a>.</li>
    <li>Improve graphics performance with <a href="http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Netbook+and+Tablet+Graphics&ProductProduct=Intel%C2%AE+Graphics+Media+Accelerator+3150+%28Intel%C2%AE+GMA+3150%29" target="_blank">Intel Graphics Media Accelerator 3150</a>.</li>
    <li>Enable multitouch support, including two-finger scrolling, with <a href="http://www.synaptics.com/support/drivers" target="_blank">Synaptics Gesture Suite</a>.</li>
    <li>Lastly, enable bluetooth with <a href="https://docs.google.com/leaf?id=0B9rTgRm4OkZwNWI4ZmMyOTUtYmZmOC00ODQ0LWExY2YtNTZjMmIyOTZiYTg5&hl=en" target="_blank">Atheros Bluetooth</a>.</li>
</ol>
</div>
Most of the hardware works out of the box, with the exception of the drivers listed above. My device was reporting a Windows Experience Index of 2.2 and the OS was running very smoothly, with Metro UI loading properly. One <strong>important</strong> tip is that because the Google Cr-48 does not have a Windows key, you will need to press either the Search key or CTRL + ESC to return to the start menu when using the Metro UI.

<br />
<br />

To restore your Cr-48 back to the default Chrome OS, follow this <a href="http://support.google.com/chromeos/bin/answer.py?hl=en&answer=1080595" target="_blank">Recovery Guide</a> from Google. Feel free to get in touch with me about any questions or concerns via Twitter.

</div>
