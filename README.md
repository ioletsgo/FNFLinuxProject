# FNFLinuxProject
So, You've decided to make a Friday Night Funkin mod,
and you need a little bit of demonstration on how you can make the mod accessible to everyone, and since the information on how to do that is sparce and scattered across several different sites and resources, with varing levels of misinformation that goes with it.

# So, Why would I do it?
- The primary reasons to do this is to ensure as good of an experience on all platforms, so issues with running could be a fault of Wine or Proton, and could negatively impact the user experience
- Latency issues can arrise from various different mods, if not coded properly or with a compatibility layer or input delay in general in mind.
- It just might not even work. Sometimes a piece of software, especially a fanmade mod with a lack of care or attention to the code can cause a piece of software to error out on attempting to run it.
- It's just good practice. To enable as many people to have the best experience, you also want to make sure that they feel acknowledged and appreciated.

# FAQ & Troubleshooting
- Q: I tried compiling to Linux on Windows, but the executable reads as a Microsoft/Windows executable on [ROM Properties](https://github.com/GerbilSoft/rom-properties) 
- A: A common issue that arises first from attempting to make a Linux port of a FNF mod through source code is that Lime compiles and creates a Windows executable in the wake of a Unix-compatible executable, which is what we are trying to avoid.

![image](https://user-images.githubusercontent.com/36903453/139360813-18f93334-a7b2-4fe9-b4c7-098439b9899c.png)

- Q: I followed the tutorial, it built properly, but running my mod through Windows, it doesn't have any audio output
- A: This isn't an issue with the compiled linux port, moreorless an issue with Windows. The default audio system that Linux uses is called PulseAudio, with Pipewire being an alternative. There isn't currently a solution to translate PulseAudio/Pipewire audio calls to the default Windows Audio Drivers, (not with a lot of tampering with your base system). The only thing that you should be worried about are constant crashes and graphical errors.

- Q: This seems a little bit hard to follow, is there an easier solution?
- A: Sure there is. If you find it difficult to grasp all of the instructions, Please contact me. I would be willing to help you make a working finished product that runs smoothly on Linux. My [twitter DMs](https://twitter.com/ioIetsgo) are always open to help.

# Requirements
The requirements varies from Windows to Linux. I'm gonna go over the more commonly used operating system, primarily because it's more complicated and that's what most FNF developers use.
## Windows
- Your Friday Night Funin Mod Source Code
- The Haxe libraries and dependencies for the source code to compile ([Base FNF](https://github.com/ninjamuffin99/Funkin), [Kade Engine](https://github.com/KadeDev/Kade-Engine/blob/stable/docs/building.md), [PsychEngine](https://github.com/ShadowMario/FNF-PsychEngine))
- [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/install) or a Linux distro running in a [Virtual Machine](https://www.virtualbox.org/) of your choosing (**WSL 2.0 RECOMMENDED**)
- A lot of time and patience.
## Linux
- Your Friday Night Funkin Mod Source Code
- The Haxe libraries and dependencies for the source code to compile ([Base FNF](https://github.com/ninjamuffin99/Funkin), [Kade Engine](https://github.com/KadeDev/Kade-Engine/blob/stable/docs/building.md), [PsychEngine](https://github.com/ShadowMario/FNF-PsychEngine))
- A lot of time and patience.
## Prerequisites
Primarily speaking for Windows, it requires a little bit more to make a linux port. A key requirement to properly make a Linux port that runs through the linux kernel, is the linux kernel itself. Now, there is an official Microsoft tutorial on how to get [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/install) running on a windows system here, I will mostly be copy-pasting how to install it onto here as well for convenience. 
# Getting Started
- [Install Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install). If you are on Windows 10 version 2004 and higher (Build 19041 and higher) or on Windows 11 (which I'm sorry for your loss), it should be as simple and easy as typing `wsl --install` into the commandline/powershell/terminal prompt, though if you're running any version older, you would have to run these commands in Powershell with Elevated or Administrator priviledges:
- - `dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart` (Enables base WSL)
- If you have the ability to run WSL 2.0 (that is, on Windows 10 Version 1903 or higher, with Build 18362 or higher on x86, and Version 2004 or higher, with Build 19041 or higher on ARM64 processors), I would run these commands with Elevated or Administrator priviledges as well:
- - `dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart` (Enables virtual machines, a necessary requirement of WSL 2.0, you have to reboot after installing it)
- - [Install the WSL2 Linux kernel update package for x64 machines and ARM64 from the Official Microsoft Website](https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package)
- Set WSL 2.0 as the default version, by using the command `wsl --set-default-version 2`
- Install your favorite distro from the [Microsoft Website](https://docs.microsoft.com/en-us/windows/wsl/install-manual#downloading-distributions) or install them via commandline by searching for them via `wsl -l -o` and installing them via `wsl --install -d <Distribution Name>`. 
- The default distribution is Ubuntu, but you can select from many several popular linux distros, like OpenSUSE, Manjaro, and Kali-Linux, just to name a few.
If everything works out, you should now be able to run the Linux Kernel while running the NT/Windows kernel.
## Linux (& Windows running WSL)
- If you're running through WSL, you will have to install Haxe using a Package manager. The distros and Package manager examples are on [the official Haxe webiste](https://haxe.org/download/linux/)
- If you have the libraries installed, you probably don't need to reinstall them, just make sure that the Haxe library directory is the same on the linux kernel compared to the windows kernel.
## Compile your FNF mod using the Linux kernel
- Compiling your mod on Linux is almost identicle to compiling it on Windows.
You go to the root of the mod and you compile using `lime build linux -final -clean`.
It should create a file in `[parent directory]/export/release/linux/bin/`, and your linux port should be in there.
