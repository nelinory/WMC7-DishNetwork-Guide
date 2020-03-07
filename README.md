# Guide for how to integrate Windows Media Center 7 with DishNetwork Satellite HD receiver

This is a guide for Windows Media Center 7 install with two tuners (Quad OTA + Colossus) hooked up to Dish Satellite VIP211K receiver.
- TV Guide comes from EPG123 (http://epg123.garyan2.net) with http://www.schedulesdirect.org subscription
- Netflix streaming supported by "NetflixMCE" by KerrAvon from https://sharepointadept.com/netflix-for-windows-media-center
- Weather forecast provided by "myForecast" by me (shameless promotion) from https://github.com/nelinory/myForecast

Final solution have been rock solid and have received 100% wife approval due to the seamless integrated functionality.

## TOC
[Revision History](#revision-history)<br/>
[Hardware Used](#hardware-used)<br/>
[Drivers Used](#drivers-used)<br/>
[Prerequisites](#prerequisites)<br/>
[Installation](#installation)<br/>
[Additional Configuration Tips](#additional-configuration-tips)

### Revision History
11/05/2019 - Initial version
<p align="right"><a href="https://github.com/nelinory/WMC7-DishNetwork-Guide#toc">Back to toc</a></p>

### Hardware Used
- ASRock FM2A75M-DGS, 8GB RAM, AMD A10-5700 (no HDMI out, using DVI-D to HDMI dongle)
- AVS Gear HA-IR01SV Infrared MCE remote with receiver (http://newegg.com)
- Dish Network VIP 211k (model VIP 211z **WILL NOT WORK** for this setup, we need component output from the receiver)
- Hauppauge WinTV-quadHD PCI Express TV Tuner Card 1609 (http://newegg.com)
- Hauppauge Colossus 01414 PCI (Colossus v1) (http://ebay.com) – comes with IR blaster and looks like this:
<p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/ColossusCard.png" alt="colossus_card" width="450"/></p>
<p align="right"><a href="https://github.com/nelinory/WMC7-DishNetwork-Guide#toc">Back to toc</a></p>

### Drivers Used
> **Note:** <br/> All provided download links are from Hauppauge website. Hauppauge driver downloads seems to be hosted on amazon.

##### Hauppauge WinTV-quadHD PCI
- Support page: http://www.hauppauge.com/pages/support/support_quadhd.html
- Windows 7 driver: https://s3.amazonaws.com/hauppauge/drivers/driver85_1_59_36248.exe

##### Hauppauge Colossus 01414 PCI
- Support page: http://www.hauppauge.com/pages/support/support_colossus.html
- Windows 7 driver: https://s3.amazonaws.com/hauppauge/drivers/colossus_1_8_31093.zip 
- Windows 7 Media Center driver: https://s3.amazonaws.com/hauppauge/hdpvr/hdpvr-colossus_mce_29271.zip
<p align="right"><a href="https://github.com/nelinory/WMC7-DishNetwork-Guide#toc">Back to toc</a></p>

### Prerequisites
- Set up your DISH satellite TV using HDMI to your HDTV.  Make sure everything is working correctly (the normal way).
<p align="right"><a href="https://github.com/nelinory/WMC7-DishNetwork-Guide#toc">Back to toc</a></p>

### Installation
>  **Attention:** <br/> Do not install the Hauppauge cards yet !
1. Perform a clean Windows 7 Home Edition Service Pack 1 install
2. Install all drivers for all devices including the video card
3. Perform full Windows Update until no new updates are found. This will require multiple restarts.
4. Disable Windows Update Service, my reasons for it - dedicated dvr, not used as desktop, behind firewall do not want surprise patches that make it unstable (or reminders to upgrade to Windows 10).

>  **Note:** <br/> The order of steps 5/6/7/8 is very important. If you install Hauppauge Colossus 01414 PCI first and then Hauppauge WinTV-quadHD PCI it will mess up the Hauppauge Colossus 01414 PCI ability to switch channels on Dish thru the IrBlaster.

5. Shutdown computer and install Hauppauge WinTV-quadHD PCI card, then power up - Windows 7 will not be able to find drivers for it. If you look in your device manager, you'll see the card is unrecognized.
6. Install Hauppauge WinTV-quadHD PCI drivers from the link [above](#drivers-used). Ensure you see the correct card listed under Device Manager/Sound, video and game controllers. There should be two entries:
```
- Hauppauge WinTV-quadHD (Model 1651xx-1, Dual ATSC/QAM, IR)
- Hauppauge WinTV-quadHD (Model 1651xx-2, Dual ATSC/QAM)
```
7. Shutdown computer and install Hauppauge Colossus 01414 PCI card, power up - Windows 7 will not be able to find drivers for it. If you look in your device manager, you'll see the card is unrecognized.
8. Install Hauppauge Colossus 01414 PCI Windows 7 driver drivers from the link [above](#drivers-used). Ensure you see the correct card listed under Device Manager/Sound, video and game controllers. There should be two entries:
```
- Colossus Capture Device
- Colossus Encoder Device
```
9. Connect the IR blaster to Colossus card by using the port that looks like a stereo mini jack. The Colossus IR blaster comes with two ends: the larger circular one is the receiver for the Hauppauge remote (we will not use it), the smaller rectangular one is what you tape to the front of the Dish Network VIP 211k. If you haven't used IR blasters before, the smaller end has a red side and a clear side with a sticky. 
<p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/ColossusIrBlaster.png" alt="colossus_ir_blaster" width="450"/></p>

10. The **Colossus Windows 7 Media Center driver package** comes with two directories: ir32 and mce. 
- Run the ir32/IR32.exe installer.  This program makes your IR blasters work. 
- Run the ir32/IRBlast.exe installer.  This program allows you to configure the IR blasters to work with Dish Network VIP 211k. 
- We'll come back later and run the mce installer !
 
11. Go to Start/Programs/Hauppauge WinTV – Run BlastCfg.  Use the following settings: 
- Region: **North America** 
- Device Type: **Satellite** 
- Vendor/Model: **Dish Network 311** (I really have a 211k, but the 311 codes work fine). 
- CodeSet: **0136** (once saved system will show it as 136)
- Click "Advanced Config".  I switched the Inter-Digit Delay to 20ms.  Click "Save Settings". 
- Click "IR Channel Test – Send". You should see the IR blaster blinking red few times.
<p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/BlasterConfiguration.png" alt="colossus_ir_blaster" width="450"/></p>

12. Remove the sticky and paste the clear side directly onto the IR receiver bulbs on the front of the Dish Network VIP 211k. Then put a piece of electrical tape over it to hold it in place. 
13. Go back to the Colossus Windows 7 Media Center driver. Run the mce/setup.exe installer. Reboot as instructed by the setup package. Ensure you see the correct device listed under Device Manager/Sound, video and game controllers. There should be one new entry:
```
- Hauppauge HD PVR Tuner Device
```
14. Connect the component cable in on the Colossus card to the 211k's component out (use the top little dongle on the card). Connect the three component outputs + the two audio outputs. I used the cable provided with Colossus card.
<p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/ColossusCables.png" alt="colossus_ir_blaster" width="450"/></p>
<p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/SatelliteReceiverPorts.png" alt="colossus_ir_blaster" width="450"/></p>

15. Go to Start/Programs/Hauppauge/HDPVR MC Setup. A dialog comes up. On the MCE Config tab, check the box for the Colossus on the left, then ensure the audio and video inputs are right (mine is Line and Component). Ensure the "Use Internal Blaster" box is checked. The source should be "Satellite". Apply the changes. Reboot again. 
<p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/HauppaugeDeviceCentral.png" alt="colossus_ir_blaster" width="450"/></p>

16. For MCE guide I use EPG123 with a schedule direct subscription (http://www.schedulesdirect.org) (yes, it is worth $25 anually !). To get the application, go to: http://epg123.garyan2.net. After downloading and installation follow the install guide of EPG123 from http://epg123.garyan2.net/install. 
>  **Note:** <br/> The following instructions **DOES NOT** supersede the EPG123 install guide, they just mention what to do in the steps within MCE setup related to Hauppauge Colossus 01414 PCI.
- Execute **step 1: Clean start** from EPG123 install guide
- Execute **step 2: TV Setup** from EPG123 install guide
  - At one-point MCE will ask you for PlayReady. Agree to the terms of service for PlayReady – you need this to record protected content. MCE will download and install PlayReady.
  - Keep in mind that the step **TV Setup/Examining TV signals** may take long time, especially with multiple tuners.
  -	After a while MCE should find a tuner called "Satellite (1 tuner)". Select: **Yes, configure TV with these results** then click Next button.
  - Click Next button again to confirm setup.
  - MCE will start searching for channels:
    - **Important:** MCE will say it is done (100%), but it's not ! **Wait ~5 minutes** to ensure that it has found all the channels. It will keep adding channels, even though it thinks it is done. 
    - It will add all the Dish Network channels (thousands), not just the ones in your package. **That's OK**. I end up with 9999 channels on the Satellite tuner.
    - Once all the channels are found click Next button.
    - Click Finish button to complete the setup.
  - I did repeat the step with TV Setup so I can configure the Hauppauge WinTV-quadHD OTA tuner too.
- Execute **step 3: Setup and Execute EPG123** from EPG123 install guide
  - Before you continue you need to have a list with all channels that are part of your Dish package. To find the list with the channels go to https://www.mydish.com.
- Finish the EPG123 installation guide

17. Start MCE. If all is good you should be able to see the correct guide for OTA/Dish HD. At this point you should be able to view/record OTA/Dish HD content. Congratulations !
<p align="right"><a href="https://github.com/nelinory/WMC7-DishNetwork-Guide#toc">Back to toc</a></p>

### Additional Configuration Tips
1. Each day at around 5:00AM, the Dish receiver calls home to get its update. It then restarts itself, requiring the user to press "Select" to go to a channel. MCE doesn't know it needs to press select, so this causes it to miss channels and recordings.
- Go to Live TV in MCE so you can see what's playing on the current Dish channel. 
- Using your Dish remote, press Menu button, then "Preferences" (option 8) and then "Updates" (option 4). Note the update time, and disable the automatic sleep. On mine, I set the update time to 5:35AM. The update usually takes ~20 minutes.
- To prevent an accidentally scheduling a recording in the "update time period" I have configured a daily manual recording schedule in MCE for the same time frame (5:30AM to 6:00AM - 30 minutes total) and set it up to keep one episode only.
- To "wake up" the receiver after update use the "HauppaugeIrBlaster" application (https://github.com/nelinory/HauppaugeIrBlaster). Configure it to run on a schedule task (with Administrator rights) every day at 6:05AM with the following parameters:
```
- HauppaugeIrBlaster.exe -w XXX (where XXX is a good channel to tune after wake up)
```

2. Dish Network VIP 211k – HTDV Setup
- Using your Dish remote, press Menu button, then "System Setup" (option 6) and then "HTDV Setup" (option 7). Ensure you have the same configuration as the below screenshot – my receiver came with default setting for TV Type as 720p.
<p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/DishHdtvSetup.png" alt="colossus_ir_blaster" width="450"/></p>
<p align="right"><a href="https://github.com/nelinory/WMC7-DishNetwork-Guide#toc">Back to toc</a></p>