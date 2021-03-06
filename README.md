= Notice =

This version of the installer is deprecated and unsupported. For the current version, please visit: https://github.com/EgoBits1/Whonix-Windows-Installer

= Introduction =

The Whonix-Installer for Windows is a simple and fast way to set-up Whonix on a system running Microsoft Windows. The following instructions will tell you how to build the Whonix-Installer for Windows using the source code provided via Github, as well as base Whonix and VirtualBox files.

= What you'll need =

* A Windows-Machine on which to do this with at least 16GB of free disk space
** Due to the fact that a big part of the build-process requires the temp folder, the space is required on the drive to which your temp folder is set
* The Whonix-Gateway and Whonix-Workstation Images for VirtualBox found here: https://www.whonix.org/wiki/VirtualBox
* The newest build of the VirtualBox-Installer found here under "Windows hosts": https://www.virtualbox.org/wiki/Downloads?replytocom=98578
* The command line based compressor 7za.exe found here under 7-Zip Extra (needs to be extracted): http://www.7-zip.com/download.html
* NSISBI, which will be used to create the installer, found here (needs to be extracted): https://sourceforge.net/projects/nsisbi/
* Whonix-UI, which can be obtained from here: https://github.com/EgoBits1/Whonix-Windows-UI/releases
** OR built from source as well via this guide: https://www.whonix.org/wiki/Building_Whonix-UI_for_Windows
* The Source for the installer, the logo and license text, found here: https://github.com/EgoBits1/Whonix-Windows-Installer-deprecated

= Preparing the files =

We start by "taking" the VirtualBox-Installer .exe "apart". This is necessary because the .exe actually contains two Microsoft Software Installation (.msi) based Installers, one for x64 and one for x86 systems, as well as a compressed .cab file. To seperate these files, we have to run the following command on the command line.

<pre>
VirtualBox[Characters based on your version].exe -extract
</pre>

Once this has been finished, a window will open telling you where these three files (VirtualBox[Characters based on your version]amd64.msi, VirtualBox[Characters based on your version]x86.msi, common.cab) have been extracted in. Rename "VirtualBox[Characters based on your version]amd64.msi" to "virtualbox_x64.msi" and "VirtualBox[Characters based on your version]x86.msi" to "virtualbox_x86.msi" and save all of them in a folder, because they will be needed later. Furthermore, put the Whonix-Workstation and Whonix-Gateway Images in the same folder and rename them "whonix_gateway.ova" and "whonix_workstation.ova" respectively.

Next up, put 7za.exe in the same folder and execute the following two commands in this directory:

<pre>
7za a gateway.7z whonix_gateway.ova
7za a workstation.7z whonix_workstation.ova
</pre>

Now you have two highly compressed 7zip files, "gateway.7z" and "workstation.7z". This is done to make the Installer as compact as is possible.

You may now remove the .ova files from the folder as they won't be needed anymore.

Now, put the source files (Whonix.nsi, logo.png, license.rtf) inside the same folder as the other files. Furthremore, include Whonix-UI (Whonix.exe).

Now, you should have the following files in the folder:

* Whonix.exe
* 7za.exe
* virtualbox_x64.msi
* virtualbox_x86.msi
* common.cab
* gateway.7z
* workstation.7z
* Whonix.nsi
* logo.ico
* license.rtf

With this, the preparation is finished and we can get on to building the Installer.

= Building the Installer =

If you recall, at the beginning I mentioned that NSISBI would be necessary. Run "makensisw" from the version of NSISBI you've obtained. Click on "File -> Load Script...", navigate to the folder you've saved the prior files in and select Whonix.nsi. This should start building the Installer. The Output can be found in the folder you've stored all the other files in named "Whonix-Installer.exe".

This concludes the guide to building the Whonix-Installer for Windows from source.
