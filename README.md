# Using ECORCE Tool on WSL2 with GUI

WSL 2 is only compatible with Windows 10/11 version 2004 build 19041 or higher. To determine the version of Windows 10 you are currently using, you can run the following command in the command prompt or PowerShell:


```
$ winver 
```

This command will open a window displaying the exact version and build number of your Windows 10/11 installation. If the version number is 2004 or higher, you can proceed with installing and using WSL 2.

<p align = "center">
  <img src="https://github.com/cmarquees/Ecorce_WSL2/assets/19821658/41fa6561-01bf-40af-a1f4-0b522bd505bf"
    
</p>

## Enabling WSL2

Depending on the version of your Windows operating system, you may need to enable specific features for WSL2. To enable WSL is very simple. Run thje following command in the command prompt or PowerShell:

```
$ dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
$ dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

After making the necessary changes for WSL 2, it is important to restart your system to ensure that the modifications take effect. Once your system has rebooted, start PowerShell with admin privileges and set WSL2 as the default version:

```
wsl --set-default-version 2
```

## Installing and configuring OS

Before starting the installation of the operating system of your choice, first check all distros supported by WSL.

```
wsl --list --online
```

In this guide, I will focus on the Debian 11 installation, but the same procedures can be applied to other OS. To download the district, we can do it through the command prompt/powershell or directly through the microsoft store.

```
wsl --install -d Debian
```
<p align = "center">
<img src=https://github.com/cmarquees/Ecorce_WSL2/assets/19821658/48c4e66b-c00d-4fa7-86ed-f68d357140ae>
</p>

After completing the download, open the debian bash by pressing the Win button and writing "Debian". Wait the system loading, register your user and then update the APT cache and upgrade all the packages.

<p align = "center">
<img src=https://github.com/cmarquees/Ecorce_WSL2/assets/19821658/4356f57a-ed48-452d-869e-25685b54fbb2>
</p>

```
$ sudo apt update && sudo apt upgrade -y
$ cat /etc/os-release
```
<p align = "center">
<img src=https://github.com/cmarquees/Ecorce_WSL2/assets/19821658/43e548b5-ad8d-407c-a114-bbe4473aca67>
</p>

## Download ECORCE tool

You can download ECORCE from your Windows platform, WSL2 allows you to exchange files between systems. Access the link below and download the version for Debian 11.
```
https://cloud.delphea.eu/index.php/s/5QneJE2S3HM82aA
```
To install the package on Debian, run the follow comand.
```
sudo dpkg -i ecorce_2.xxRxxxx-debian11_amd64.deb
```
There will probably be dependences to be addressed. To fix them, run the following command.
```
sudo apt --fix-broken install
```
Now if you run ECORCE, in your Debian terminal, a graphical window would open. However, a error related to D-bus will cause the window to close. To handle this, run the following command.
```
sudo service dbus start
```
Now we have finished the installation, write ECORCE again and enjoy.

<p align = "center">
  <img src=https://github.com/cmarquees/Ecorce_WSL2/assets/19821658/90ffd50a-6dfd-41a5-aa63-28d9687d8a66>
</p>
