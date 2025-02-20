---
id: GUIDocs
title: The OpenBCI GUI
---

![image](assets/SoftwareImages/OpenBCISoftware/GUI-V4-Screenshot.jpg)

The OpenBCI GUI is OpenBCI's powerful software tool for visualizing, recording, and streaming data from the OpenBCI Boards. Data can be displayed in live-time, played back, saved to your computer in .txt format, as well as streamed in live-time to third-party software such as MATLAB. 
It can be launched as a standalone application or as a sketch from Processing (a Java-based programming language). In this guide, we will cover both scenarios.

## Hardware/Driver Setup for OpenBCI_GUI

Shown below are the three OpenBCI Boards that can be used with the OpenBCI GUI.

![image](assets/SoftwareImages/OpenBCISoftware/labelledBoards.jpg)

### Cyton and Cyton+Daisy on macOS/Windows/Linux
If it’s your first time working with OpenBCI and you own the Cyton or Cyton+Daisy, [make sure to install the latest FTDI driver](https://www.ftdichip.com/Drivers/VCP.htm) for your operating system. This installation is required to establish a clean connection with the OpenBCI Cyton and Cyton+Daisy hardware. 


### Ganglion on macOS/Windows/Linux

**The OpenBCI Ganglion uses Bluetooth LE (aka Bluetooth Smart, Bluetooth 4.0). In order to use the Ganglion, you need a [small USB Dongle](https://shop.openbci.com/products/ganglion-dongle).**

*Note: The [CSR Dongle](https://github.com/openbci-archive/Docs/blob/master/Deprecated%20Docs/Setup_CSR_Dongle.md) is no longer supported.* We recommend using the [newer Ganglion Dongle](https://shop.openbci.com/products/ganglion-dongle).

### WiFi Shield

There are no prerequisites for running the WiFi Shield with Cyton or Ganglion on macOS/Windows/Linux, move on to the installation section below.

### Linux Users: Serial Port Permissions

<p><details><summary><b><i>Attention Linux Users: Expand this dropdown for important details. This fix affects all communications between Ganglion/Cyton and your computer via serial ports.</b></i></summary><br>

Before trying to connect to any OpenBCI boards on Linux, you need to make sure you have permission to access the serial ports on your machine. Otherwise, you will get the error `Failed to connect using /dev/ttyUSB0` or similar. This can be fixed by adding the user to the `dialout` group in Ubuntu. Here is a [full explanation and fix](https://websistent.com/fix-serial-port-permission-denied-errors-linux/). Here is the short version:<br><br>

1. First, verify if the user does belong to the "dialout" group using the “id” command.<br>
&nbsp;&nbsp;&nbsp;&nbsp;- Type `id -Gn <username>` in terminal and check if it prints `dialout` as one of the options.<br>
&nbsp;&nbsp;&nbsp;&nbsp;- Replace <username> with your Linux username. Example: `id -Gn susieQ`<br>
2. Next, add the user to the “dialout” supplementary group.<br>
&nbsp;&nbsp;&nbsp;&nbsp;- Type `sudo usermod -a -G dialout <username>` in terminal.<br>
&nbsp;&nbsp;&nbsp;&nbsp;- Example: `sudo usermod -a -G dialout susieQ`<br>
3. Restart Ubuntu<br>
4. Try "id" command again<br>
&nbsp;&nbsp;&nbsp;&nbsp;- Repeat step one<br>
</details></p>

## Installing the OpenBCI GUI as a "Standalone" Application

### Download the Appropriate Application For Your OS

The fastest way is to download the standalone .exe/.app for your machine and operating system. To do this, head to the [Downloads](http://openbci.com/donation) page of the OpenBCI website, and click the download link that correlates to your OS and machine.

![image](../../assets/SoftwareImages/OpenBCISoftware/DownloadsUpdated.png)

### Install OpenBCI_GUI On macOS

Drag and drop the `OpenBCI_GUI` application to you `Applications` folder.

![Drag and drop application](assets/SoftwareImages/OpenBCISoftware/gui_drag_and_drop.png)

### Install OpenBCI_GUI On Windows

Move the `OpenBCI_GUI` directory anywhere you like.

<details><summary><i>Windows Users: How to run the GUI with High DPI Screens</i></summary>

<br>If you have a high DPI screen and are running Windows 10, you may notice that the GUI is hard to see, and nothing seems to scale correctly.<br>

1. First, close the GUI if it is open.<br>

2. Next, right click on `OpenBCI_GUI.exe` and select `Properties`. The following window should pop up:<br>

![gui windows properties menu](../../assets/SoftwareImages/OpenBCISoftware/GUI-WindowsProperties.png)<br>

3. Select the `Compatibility` tab at the top of this window, and then click `Change high DPI settings`.<br>

![gui windows properties compatibility](../../assets/SoftwareImages/OpenBCISoftware/GUI_WindowsProperties_Compatibility.png)<br>

4. In the section labeled `High DPI scaling override`, check the box `Override high DPI scaling behavior` and change from `Application` to `System (Enhanced)`.<br>

![gui windows override high dpi scaling](../../assets/SoftwareImages/OpenBCISoftware/GUI_Windows_OverrideHighDPI.png)<br>

5. That's it! Once the settings have been changed, restart the GUI!

</details>

### Install OpenBCI_GUI On Linux

<p>Unzip the downloaded application and place in desired location.</p><br>

<p><details><summary><i>Linux Users: How to run the GUI with High DPI Screens</i></summary>

On Linux, there is no way to force scaling. However, here is a <a href ="https://github.com/kaueraal/run_scaled">link to a script that should work</a>.

</details></p>

## Running the OpenBCI_GUI

**Important Notes:**

 * In some cases, there may be issues with the way your machine handles the BLE application that enables communication with the Ganglion Board.
 * If you run into additional issues, please visit the [OpenBCI_GUI Section](https://openbci.com/forum/index.php?p=/categories/openbci_gui) of our Forum

### Running on macOS

Navigate to your `Applications` folder and double click the `OpenBCI_GUI` You may see a message pop up asking you if you're sure you want to open it. Click Open and the app will launch.

![allow GUI to run](../../assets/SoftwareImages/OpenBCISoftware/ganglion_permissions.png)

### Running on Windows

Navigate to your `OpenBCI_GUI` directory, double click `OpenBCI_GUI.exe`.

### Running on Linux

Open a terminal application and navigate to the directory (with `cd`) of the unzipped application.

Then, launch the Application from terminal with the command:

```
$ ./OpenBCI_GUI
```
or
```
$ sudo ./OpenBCI_GUI
```

This will launch the OpenBCI_GUI. **If you experience issues, try running with or without `sudo`.**

## Using the OpenBCI GUI

### BrainFlow Java Library

**Starting with GUI v5, simply run the GUI and connect to all OpenBCI hardware!** In the background, we are using the included [BrainFlow Java library](http://docs.openbci.com/docs/11ForDevelopers/SoftwareDevelopment#brainflow---java) to handle communications with the boards.

### Tutorial

![use gui](../../assets/SoftwareImages/OpenBCISoftware/USE-GUI.jpg)

Check out this [Youtube video](https://www.youtube.com/watch?v=agV1B2l-QLw) on how to use the OpenBCI GUI. Note: Uses an older version of the GUI.

### Data Log Options

Users have the option to save data as a CSV text file or BDF+ format. **By default, the GUI stores all user data and raw EEG recordings in `[USER]/Documents/OpenBCI_GUI` and names each session with an autogenerated timestamp by default.** Older versions of the GUI save data to `SavedData` in the same root directory as the app.

Cyton users can save data to an SD card. To playback these files using the GUI, copy these files to your computer from the SD card. This works better than reading files from the SD card. With GUI v5, it is no longer necessary to convert SD files for playback in the GUI. A few users may still want to [convert large SD file recordings](#converting-large-sd-card-recordings).

### Customize Your Layout

The OpenBCI GUI displays up to six customizable windows in twelve layouts! You can choose what each window displays by clicking the dropdown menu at the upper left of each window. The bottom row of layouts work best on higher resolution monitors.

![GUI Layout Dropdown Screenshot](../../assets/SoftwareImages/OpenBCISoftware/GUIv5_LayoutSelector_Highlighted.png)


### Impedance Testing
When using Cyton, you can display the impedance of individual channels by toggling the small Ohm icon to the right of each color coded channel number in the Time Series Widget. When the Ohm icon is toggled on, the board sends a small current through the selected channel to obtain the impedance value. **For this reason, you won't be able to stream data on a channel and obtain the impedance value simultaneously.**

In the screengrab below, the GUI is showing Time Series, FFT Plot, and Accelerometer. Also, you can see an impedance test has been started on Channel 1.

<img src="https://github.com/openbci-archive/Docs/blob/master/assets/images/GUI_Impedance.png?raw=true" width="100%">

To test impedance for Ganglion, use the Ganglion Signal Widget.

<img src="https://github.com/openbci-archive/Docs/blob/master/assets/images/ganglion_signal_widget-impedance_check.png?raw=true" width="50%">

### Decrease Setup Time by Saving/Loading Settings
Starting with GUI V3, you can save and load a snapshot of nearly every setting in the GUI (ex. Layout, Time Series Channel Settings, Networking Settings, etc.) by using a dropdown menu (pictured below) or keyboard shortcuts. If you change anything during a session, save your settings or click "Stop System" before exiting. __Save with lowercase 'n'__ and __Load with capital 'N'__ on your keyboard to and from */Documents/OpenBCI_GUI/Settings/*.

![Config Button](../../assets/SoftwareImages/OpenBCISoftware/GUI_Config_Button_ScreenshotRev3.png)

Start the system first. Then, arrange the GUI to suit your needs and __click "Settings"-->"Save"__. A dialog box will open to confirm file name and path _(e.g. GanglionUserSettings.json)_. After, you will see a message saying "Settings Saved!" When you click "Stop System", all settings will be auto-saved.

The GUI automatically loads settings from */Documents/OpenBCI_GUI/Settings/* when the system starts!

To load settings, just __click "Settings"-->"Load"__. Select a settings file from the dialog box that opens. If the settings are incompatible (ex. loading 16 channels while using 8), the GUI will display an error at the bottom or "Default Settings Loaded". If all is well, the GUI will display "Settings Loaded!" as the GUI snaps directly to your desired settings.

__Click "Settings"-->"Default" to revert the GUI to default settings.__

For all data modes, the GUI will load all GUI-related settings automatically. After starting a session, hardware settings (channel on/off, gain, etc.) will need to be set by the user manually.

### GUI Keyboard Shortcuts
__Use the spacebar to start or stop the data stream!__

#### Expert Mode

__To enable all keyboard shortcuts, set "Expert Mode On" in the settings dropdown.__ This mode is off by default to prevent accidentally sending a command to the board.

![Expert Mode Button](../../assets/SoftwareImages/OpenBCISoftware/expertModeToggleHelpText.png)

Expert Mode Keyboard Shortcuts:

- Other than spacebar, you can press 's' to stop data stream, and 'b' to begin, or start the data stream.

- You can _use lowercase 'k' to set "Bias Don't Include"_ on all channels, or _lowercase 'l' to set "Bias Include"_ on all channels.

- __Press lowercase 'd' to set all channels settings to default.__

- Using an _English keyboard_, you can deactivate channels 1-16 using:
  - 1,2,3,4,5,6,7,8
  - q,w,e,r,t,y,u,i

- Similarly, activate channels 1-16 using:
  - !, @, #, $, %, ^, &, *
  - Q,W,E,R,T,Y,U,I

- __Take a screenshot of the GUI using lowercase 'm'!__ It will be saved to */Documents/OpenBCI_GUI/Settings/*.

- __Enter presentation mode using Enter (Win), or Return (Mac).__

- To change to the alternate color scheme, use '{'.

## Running the OpenBCI GUI from the Processing IDE

**Most users should start by [running the standalone OpenBCI GUI](#running-the-openbci_gui). The Processing IDE is for adding features, modifying existing code, or testing development versions.**

The OpenBCI GUI was built using [Processing](https://processing.org/), a popular, Java-based creative coding framework. If you are interested in adding features or modifying the existing code, it is really easy to do so if you are familiar with Java. If you're not familiar with Java, don't fret! Processing is one of the easiest software packages to pick up as a beginner coder.


The things you will need to run the OpenBCI GUI in Processing are:  

 * [Processing App](https://processing.org/download/?processing)
 * [OpenBCI GUI Sketch](https://github.com/OpenBCI/OpenBCI_GUI)

First, go to processing.org and download the latest version of Processing. [Here is a walkthrough on how to install Processing on Ubuntu Linux.](http://www.artsnova.com/processing/installing-processing-ubuntu-linux-tutorial.html)

Go ahead and move it to your `Applications` folder, and launch the application. If this is the first time that you are running Processing, it will create what it calls it's `Sketch` folder in the following locations:  

 On a Mac `Users/<user-name>/Documents/Processing`  
 On Windows `C:\Users\<user-name>\Documents\Processing`  
 On Linux `/home/<user-name>/sketchbook`  

![GUI repo](../../assets/SoftwareImages/OpenBCISoftware/ganglion_GUI-repo.png)

The OpenBCI GUI code repository is located on github [here](https://github.com/OpenBCI/OpenBCI_GUI). click on the `Clone or download` button in green on the right, and select `Download ZIP`. If you are a advanced GitHub user, go ahead and clone it, or fork it if you like.

After the download completes and the file extracts itself, you will see the folder called `OpenBCI_GUI-master`. Change the name of this file to `OpenBCI_GUI`. If you don't change it, it won't work! You can move the folder `OpenBCI_GUI` and it's entire contents to your Sketch folder, or put it wherever you like (Mac Example: `Users/<user-name>/Documents/GitHub/OpenBCI_GUI`).

![libraries folder](../../assets/SoftwareImages/OpenBCISoftware/ganglion_libraries-folder.png)

Inside the `OpenBCI_GUI` folder, there is a folder called `libraries`. Theses are the 3rd party libraries that the OpenBCI GUI uses to work it's magic. You need to **copy** all of these folders into:

On a Mac `Users/<user-name>/Documents/Processing/libraries`  
On Windows `C:\Users\Username\Documents\Processing\libraries`  
On Linux `/home/<user-name>/sketchbook/libraries`

If there is no folder called `libraries` in that location, go ahead and make one. Once you have done that, close the Processing app and reopen it. If you get an error saying "Duplicate Packages", you may need to remove the `jna` package from the `Processing\libraries` folder.

### Open The OpenBCI GUI Project in Processing & Launch It!

![processing startup](../../assets/SoftwareImages/OpenBCISoftware/ganglion_processing-launch.png)

**If you are on Windows, set Processing to 'Run this program as an administrator'.**

When you get Processing running again, you will see a window open up. This is the Processing IDE (Integrated Development Environment).

![Select Sketchbook](../../assets/SoftwareImages/OpenBCISoftware/ganglion_file-sketchbook.png)
![Select OpenBCI GUI from Sketchbook](../../assets/SoftwareImages/OpenBCISoftware/ganglion_sketchbook-window.png)

Select `File > Sketchbook` and you will open a window where you should see the option to select `OpenBCI GUI`. When you get that far, select `OpenBCI GUI` and the Processing will open up yet another window, that contains all the code to successfully run the OpenBCI GUI.  

![GUI code window](../../assets/SoftwareImages/OpenBCISoftware/ganglion_GUI-code-window.png)

If you don't know anything about coding, don't edit these files. If you like to dig in to the meat of what makes things work, by all means. have at it. You are looking at the program code that makes the OpenBCI GUI work it's magic. Now, it's time to run it!

![Processing RUN](../../assets/SoftwareImages/OpenBCISoftware/ganglion_processing-RUN.png)

Press the `play` button on the upper left of the IDE, and the sketch will try to launch! 

If you are encountering issues launching the GUI at this point, please head to the [OpenBCI_GUI section](https://openbci.com/forum/index.php?p=/categories/openbci_gui) of our Forum and look for help or post a question.

## Converting Large SD Card Recordings

**Note: This can only be done with GUI v4.2.0 or earlier.** In order to convert large SD card recordings made using Cyton or Cyton+Daisy, you will need to run the GUI from Processing, but we need to change one crucial setting in Processing's Preferences. As mentioned in the screenshot below, open Processing preferences and increase max available memory to at least 9GB to convert a 12 hour SD recording. Click OK to save these preferences, restart Processing to make sure the changes take effect, and re-launch the GUI.

![GUI Screenshot convert large SD recording](assets/SoftwareImages/OpenBCISoftware/gui_convert_large_SD_recordings_scrnshot.png)
