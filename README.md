# SDSoC Virtual Machine Installation Guide

## Prerequisite

1. Ram >= 12G

   We need enough ram to run our Windows and the virtual machine. For the best experience, we need to give 8G to the virtual machine to run the SDx and 4G to our Windows.

2. CPU Virtualization Enabled

   You can check this in your task manager on the CPU page. If you have not enabled this option and have no idea about how to enable it, you can search it by google, since this step is different on different computers.

3. Rom >= 100G

## Environment

1. VMware Workstation Player 15

2. CentOS 7.6.x

3. SDSoC 2018.3

## Download

> VMware Workstation Player
>
> https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html
>
> Centos
>
> http://mirror.datto.com/CentOS/7.6.1810/isos/x86_64/CentOS-7-x86_64-DVD-1810.iso
>
> SDSoC
>
> https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/sdx-development-environments/2018-3.html
>
> For SDSoC, you need to register a Xilinx account first. You can download the SFD or web installer version. I use SFD version as an example here.

## Important steps

### Install VMWare Workstation

You can install it in any place you want. I just install it at the default position.

### Create virtual machine

Create the virtual machine with the downloaded CentOS ios file, you can almost follow the steps of the VMware and just modify some parameters.

1. Change the installation place. For the best experience, choose a solid drive as your installation place. 

2. change the disk driver size from the default 20G to 100G(or more). I change it to 230G here.

3. Customize your hardware. Change ram to 8G, CPU to your actual CPU's core count and **USB controller to USB 3.0**. This step is very **IMPORTANT**.

## Install the CentOS system

CentOS does not support AutoInstall, so we need to install it manually.

1. Choose 'install centos7'.

2. Choose your language and I choose English as an example here.
3. Now the home page should be

![](https://raw.githubusercontent.com/zequyou/Gallery/master/img/20190831082050.png)

4. click 'SOFTWARE SELECTION' and do what I do show on the image. Click Done and go back to the home page.

![](https://raw.githubusercontent.com/zequyou/Gallery/master/img/20190831082304.png)

5. Click 'INSTALLATION DESTINATION', click the blue area and click done.

![1567254293867](C:\Users\zequy\AppData\Roaming\Typora\typora-user-images\1567254293867.png)

6. You can click the 'NETWORK & HOST NAME' icon and set up your network. This step is not necessary.
7. Click 'Begin Installation' and begin the installation process.
8. Click 'ROOT PASSWORD' to set your system root user password.
9. Click 'USER CREATION' to create your user name and password. The only thing I need to mention is that **you should make this user administrator**. I use the developer as the example user name.

![](https://raw.githubusercontent.com/zequyou/Gallery/master/img/20190831082800.png)

10. Wait until centos installation complete.

![](https://raw.githubusercontent.com/zequyou/Gallery/master/img/20190831082955.png)

It tells you the progress.

11. Install VMware tools. These tools will allow you to copy and paste something from the host machine to the virtual machine and share the disk space. Click 'Player(P)', choose Management and click 'Install VMware tools'.

![](https://raw.githubusercontent.com/zequyou/Gallery/master/img/20190831083810.png)

12. Open the VMware Tools disk on the desktop. Decompress the only one tar.gz file inside it. Follow the instruction inside it to install the tools.
13. Click 'Player(P)', choose Management and click 'Virtual Machine Settings'. In the options page, share your dir where you have the SDSoC installation file. Then, in the /mnt, you will find the dir you just set.
14. Install SDSoC with the official guide https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_3/ug1238-sdx-rnil.pdf. **Do not forget to install the cable driver**. I recommend you to install it inside your home dir and do not install it as root.
15. Set the license in ~/.bashrc file. Add the following line to the end of this file  ```export XILINXD_LICENSE_FILE=???``` (You can find ??? content in the first assignment document.).  Run command ```source ~/.bashrc```.

16. run command ```sudo usermod -a -G dialout,audio YOUR_USER_NAME```. Change YOUR_USER_NAME to the user name you create on step9. For me, it is developer.
17. Reboot your virtual machine.
18. Enjoy your virtual machine SDSoC environment.

## Q&A

### Why CentOS?

I choose ubuntu before. However, the doc nav never works.



