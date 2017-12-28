# FRCSim-Tutorial
1923 Installation Guide: FRCSim

Requirements:

- Either Mac or Linux(linux is recommended).

- Gazebo, and in turn FRCSim does not run on Windows!
- A reliable and fast internet connection.
- You will need to download massive amounts of software.
- A fairly recent computer. 
- As a general rule, remember that FRCSim runs slightly slower than a demanding game.
- Things To Remember:
  - Run these steps in the specified order.
  - Wait for a step to finish before moving on.
  - A step may perform unexpected actions, so you should always wait for it to finish.
  - Read the instructions completely before running a command

**AVOID VMs AT ALL COSTS!!!!!!**

***

Setting Up FRCSim:
- First you need to dual-Boot your computer with Ubuntu 16.04.3 LTS 
  - You should first download Ubuntu from Canonical [here](https://www.ubuntu.com/download/desktop)
  - Once you have downloaded the .iso file, burn the file to a usb flash drive which should have at least 2 GB
  - Create a live USB by writing the iso to the usb:
    - [Windows instructions](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
    - [OS X instructions](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
 - ONLY If you have previously tried to dual-boot a computer or have made recovery partitions, you will need to do this step to delete them. Press the start button, type in partition, open up disk management, delete all extraneous partitions you should only have these 2: 
<pre>Windows C:
EFI System Partition</pre>

- Open up hard drive manager and either shrink partition of windows on your C: drive or make sure you have a drive inserted that is completely empty
- Boot up the live usb. Reboot your computer and press F9 (the keyboard key may vary from computer to computer) repeatedly after rebooting until you see the boot manager menu. Boot from the UEFI USB stick OS.
- Try ubuntu(if you have done this before, you can go straight to setting it up). You may have some wireless problems on a hp as they are known for having wifi driver issues, if so don’t worry just use an ethernet cable or move right next to your router (while booted in ubuntu)
- **If everything works**, download ubuntu. There should be a shortcut to the installer on the desktop. Just do everything the installer says and you should be able to boot into ubuntu by pressing F9 (the keyboard key may vary from computer to computer) repeatedly after rebooting until you see boot manager, then choose the option with ubuntu on it

Once Ubuntu has loaded up,
- Disable safe boot on your computer

Once ubuntu is installed,
- Tap the windows button (in this FRC guide we will refer to it as the ‘super’ button)

Type in:
<pre>Ubuntu Software</pre>
Type in:
<pre>GDebi</pre>
Install the first one

Optional - Download Google Chrome **(recommended)**:
https://www.google.com/chrome/browser/desktop/index.html

Download WPILib (downloading WPILib is a bit different on ubuntu): as you have to add a repository first:
- Open terminal(ctrl +alt+t) then type:
<pre>sudo apt-add-repository ppa:wpilib/toolchain</pre>

Then you need to add java (warning: you will get a deprecation notice, but ignore it):
<pre>sudo add-apt-repository ppa:webupd8team/java</pre>

Once (all of the above is done run the following command - you should see all of the packages that you just installed in the terminal as ubuntu shall have refreshed!):
<pre>sudo apt-get update</pre>

Now, paste the following command as is:
<pre>sudo apt-get install \
  git \
  libc6-i386 \
  curl \
  jstest-gtk gradle oracle-java8-installer \
  frc-toolchain meshlab cmake libprotobuf-dev \
  libprotoc-dev protobuf-compiler</pre>

Not necessary for most installations The $HOME/Downloads directory should already exist on your Ubuntu machine, but this will create it if it is not present.
<pre>mkdir -p $HOME/Downloads</pre>

Now we will edit the file /etc/environment.
<pre>sudo nano /etc/environment</pre>

Append a new line with this content. This defines a system-wide variable named JAVA_HOME that references the install location of Java on your machine.
<pre>JAVA_HOME="/usr/lib/jvm/java-8-oracle"</pre>

**<mark>Immediately</mark> load the /etc/environment configuration file you just created.**
<pre>source /etc/environment</pre>

List the contents of your Java installation directory using your new $JAVA_HOME variable.
<pre>ls $JAVA_HOME</pre>

You should see contents like this, which means that your system is properly referencing the Java installation directory we set above.

|      like     |              this                |
| ------------- |:--------------------------------:|
|bin            |LICENSE                           |
|COPYRIGHT      |man                               |
|db             |README.html                       |
|include        |release                           |
|javafx-src.zip |src.zip                           |
|jre            |THIRDPARTYLICENSEREADME-JAVAFX.txt|
|lib            |THIRDPARTYLICENSEREADME.txt       |

Installing Eclipse
- Install eclipse only from the official source:
https://www.eclipse.org/downloads/download.php?file=/oomph/epp/oxygen/R2/eclipse-inst-linux64.tar.gz

(Click the orange button on the above website)

- Open the folder in nautilus (files)
- Right click the folder with the .tar.gz extension and click extract here
- Open the eclipse-installer directory and double-click the eclipse-inst installer to being the installation process.
- When prompted, select Eclipse IDE for Java Developers as the flavor of Eclipse that we want.
- Note that Eclipse will be installed to $HOME/eclipse/java-oxygen by default. The install location should not matter. You can change it, but I recommend leaving it alone unless you know what you are doing.
- Follow the prompts to install Eclipse, and then Launch Eclipse after the installation is finished.
- When prompted to choose a workspace, use the default value and click Ok unless you know what you are doing. The workspace is the directory where Eclipse will save your programming projects, and defaults to $HOME/workspace. Once again, You can change it, but I recommend leaving it alone unless you know what you are doing.

Check on a couple of configuration options in Eclipse.
- On the menu bar, go to: `Window -> Preferences -> Java -> Installed JREs`
Make sure the Oracle JDK8 is listed.
Go to: Window -> Preferences -> General -> Workspace
Check Save automatically before build.
Note that, if you used all the default settings, Eclipse should now be installed at $HOME/eclipse/java-oxygen/eclipse.

Install Eclipse FRC Plugins
First we shall install CTRE Toolsuite
Since you are not on windows, you MUST use the following link: http://www.ctr-electronics.com//downloads/lib/CTRE_FRCLibs_NON-WINDOWS_v4.4.1.14.zip
Once installed, extract to wherever you want (personally i recommend $HOME)
Now open eclipse (we will get back to CTRE Toolsuite later)
Now we will install the Eclipse FRC plugins. The Eclipse plugins for FRC assist you in building, deploying, and testing Robot projects. Be sure that you do not interrupt this process. It may seem to hang or freeze at times (especially on a slow machine), but let it take the time it needs.
Help -> Install new software -> Add…
Use the following settings.
Name: FRC Plugins
Location: http://first.wpi.edu/FRC/roborio/release/eclipse/
Click Ok
Expand the WPILib Robot Development repo.
Check the box for the Robot Java Development plugin.
Click Next, and follow the wizard and confirm and agree to the prompts presented to you.
You may see a message that says Warning: You are installing software that contains unsigned content. Although this is not ideal, it is safe to click Ok.
Eclipse will prompt you to restart itself. Let it.
Eclipse will install critical files after it restarts.

Install Gazebo - 
Gazebo (the simulator software) allows you to test your robot code in a (modeled) 3D space.
Just run the following command in terminal:
<pre>curl -ssL http://get.gazebosim.org | sh</pre>

Install FRCSim
> “With FRCSim, you should be able to finish 90% Of your programming without ever touching a RoboRIO. We want you to be able to test your code BEFORE you put in on your robot, and before the robot is even built. FRCSim allows robot code written in C++ or Java that normally runs on your RoboRIO to be run on your laptop or desktop. It connects to custom robot models in the Gazebo robot simulator.“ [3]

Use curl to download FRCSim files to your machine.
<pre>curl -o \
    $HOME/Downloads/simulation-2017.2.1.zip                                      http://first.wpi.edu/FRC/roborio/maven/release/edu/wpi/first/wpilib/simulation/simulation/2017.2.1/simulation-2017.2.1.zip</pre>
Create a directory for various simulation files. Note that Eclipse automatically created $HOME/wpilib when we installed the FRC Plugin. We are now manually creating $HOME/wpilib/simulation.
mkdir $HOME/wpilib/simulation
Unzip our simulation files to the directory we just created.
<pre>unzip \
    $HOME/Downloads/simulation-2017.2.1.zip \
    -d $HOME/wpilib/simulation</pre>
Create a system-wide symlink to the frcsim (FRC simulator) program.
<pre>sudo ln -s $HOME/wpilib/simulation/frcsim /usr/bin/frcsim</pre>
Create a system-wide symlink to the sim_ds (simulated driver station) program.
<pre>sudo ln -s $HOME/wpilib/simulation/sim_ds /usr/bin/sim_ds</pre>
We must manually compile the wpilib simulation plugins for FRCsim in order for the simulator to work properly on Linux. 

Navigate to the $HOME/Downloads directory in your terminal.
<pre>cd $HOME/Downloads</pre>
Use git to download some wpilib code that we must compile on our machine.
<pre>git clone https://github.com/wpilibsuite/allwpilib</pre>
Navigate to the allwpilib code that we just downloaded.
<pre>cd $HOME/Downloads/allwpilib</pre>
Check out a specific version of the code we just downloaded.
<pre>git checkout v2017.3.1</pre>
Run the gradlew script. That script will use gradle, a software build tool, to compile the software we just downloaded. This script takes a while to run. Though, occasionally, I see this script freeze and hang. If that happens, it is safe to kill this and re-run it.
<pre>./gradlew build -PmakeSim</pre>
Copy the plugins we just compiled into our simulation plugins directory.
<pre>cp ./build/install/simulation/plugins/* \
    $HOME/wpilib/simulation/plugins/</pre>

Install model and world files
2018 simulation files have not yet been released (and the 2017 files were never shared either) but we can install the 2016 simulation worlds and models to give us something to work off. Download some 3D models for our simulation.
<pre>curl -o \
    $HOME/Downloads/models.zip \    https://usfirst.collab.net/sf/frs/do/downloadFile/projects.wpilib/frs.simulation.frcsim_gazebo_models/frs1160?dl=1</pre>
Unzip the model files into our $HOME/Downloads directory.
<pre>unzip $HOME/Downloads/models.zip -d $HOME/Downloads/</pre>
Copy the downloaded gazebo simulation models into our simulation directory.
<pre>cp -r $HOME/Downloads/frcsim-gazebo-models-4/models \
    $HOME/wpilib/simulation/</pre>
Copy the downloaded gazebo simulation worlds into our simulation directory.
<pre>cp -r $HOME/Downloads/frcsim-gazebo-models-4/worlds \
    $HOME/wpilib/simulation/</pre>
Download the official 2016 game arena world file to our simulation directory.
<pre>curl -o $HOME/wpilib/simulation/worlds/frc2016.world \
    "http://first.wpi.edu/FRC/roborio/release/simulation/downloads/frc2016.world"</pre>

Create a sample application
In eclipse:
Eclipse -> New -> Other -> Example Robot Java Project -> GearsBot -> Finish.
Run

1. FRCSim/Gazebo
You only need to do this step once: Fire up frcsim (Gazebo) using the terminal.
<pre>frcsim</pre>
Wait until Gazebo has finished loading. Once Gazebo loads, insert the sample GearsBot robot provided by FRC.
Gazebo -> Insert -> Models -> GearsBot
Click somewhere in the world to place your model.
Close everything open right now

Running Auton
You only need to do this step once: install the 2016 field
<pre>curl -o $HOME/wpilib/simulation/worlds/frc2016.world \
    "http://first.wpi.edu/FRC/roborio/release/simulation/downloads/frc2016.world"</pre>
First open eclipse and run a eclipse 2016 prgm as a simulated robot deployment
then type:
<pre>frcsim $HOME/wpilib/simulation/worlds/frc2016.world</pre>
then place the robot in the field
then type in: 
<pre>sim_ds</pre>
then click auton
Then click enable
You auton code should be simulated

Troubleshooting:
If robot isn’t moving:
Just put allwpilib in $HOME/downloads and the simulation folder i sent in $HOME/wpilib/simulation
Download links
[allwpilib](https://drive.google.com/file/d/1r7OACq7wfMrDpYKhzfQyqQ1FASNpL6Kt/view)
[Simulation](https://drive.google.com/file/d/1m65NDMDnk5CLKA_qtWDlXYtBQY9ZIAkw/view)
Then move the libgz_msgs from the build in allwpilib to plugins in your wpilib/simulations folder

[Err] [Master.cc:96] EXCEPTION: Unable to start server[bind: Address already in use]. There is probably another Gazebo process running, so you just need to restart your computer

If eclipse isn’t working
Use ant to build

<p align="center">
<img src="https://lh6.googleusercontent.com/bC9IZw4vcDQaAW5zS-yXITbiDdfhunJEOVKK07VPs9uwrdEgCUFRUusQAZbaR2ynpfnyjEYcleRYWp2AMbZ-MMSD1Sif_s5uqxaxTnDQ5IQh8aqO2MtyfLnhjsoPrEcKF7sKvFDh" width="200" height="200" alt="MidKnight Inventors">
</p>

Sources: 
- Installing Ubuntu: [[1]](https://wpilib.screenstepslive.com/s/currentCS/m/frcsim/c/84464) [[2]](https://help.ubuntu.com/community/WindowsDualBoot)
- Setting up FRCSim and dependencies: [[3]](http://willhaley.com/blog/frc-linux/#install-and-configure-prerequisites
- Running FRCSim: [[4]](https://wpilib.screenstepslive.com/s/currentCS/m/frcsim/l/228983-simulating-pacgoat-with-frcsim)
