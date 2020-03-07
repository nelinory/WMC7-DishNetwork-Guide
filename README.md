# Guide for how to integrate Windows Media Center 7 with DishNetwork Satellite HD receiver

This is a guide for Windows Media Center 7 install with two tuners (Quad OTA + Colossus) hooked up to Dish Satellite VIP211K receiver.
- TV Guide comes from EPG123 with subscription to http://www.schedulesdirect.org
- Netflix streaming supported by "NetflixMCE" by KerrAvon from https://sharepointadept.com/netflix-for-windows-media-center
- Weather forecast provided by "myForecast" by me (shameless promotion) from https://github.com/nelinory/myForecast

Final solution have been rock solid and have received 100% wife approval due to the seamless integrated functionality.

## TOC
[Revision History](#revision-history)<br/>
[Hardware Used](#hardware-used)<br/>
[Drivers Used](#drivers-used)<br/>
[Prerequisites](#prerequisites)<br/>
[Installation](#installation)<br/>

### Revision History
11/05/2019 - Initial version
<p align="right"><a href="https://github.com/nelinory/WMC7-DishNetwork-Guide#toc">Back to toc</a></p>

### Hardware Used
- ASRock FM2A75M-DGS, 8GB RAM, AMD A10-5700 (no HDMI out, using DVI-D to HDMI dongle)
- AVS Gear HA-IR01SV Infrared MCE remote with receiver (http://newegg.com)
- Dish Network VIP 211k (model VIP 211z **WILL NOT WORK** for this setup, we need component output from the receiver)
- Hauppauge WinTV-quadHD PCI Express TV Tuner Card 1609 (http://newegg.com)
- Hauppauge Colossus 01414 PCI (Colossus v1) (http://ebay.com) – comes with IR blaster and looks like this:
<p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/ColossusCard.png" alt="colossus_card" width="400"/></p>
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

5. Shutdown computer and install Hauppauge WinTV-quadHD PCI card, then power up - Windows 7 will not be able to find drivers for it. If you look in your device manager, you’ll see the card is unrecognized.
6. Install Hauppauge WinTV-quadHD PCI drivers from the link [above](#drivers-used). Ensure you see the correct card listed under Device Manager/Sound, video and game controllers. There should be two entries:
```
- Hauppauge WinTV-quadHD (Model 1651xx-1, Dual ATSC/QAM, IR)
- Hauppauge WinTV-quadHD (Model 1651xx-2, Dual ATSC/QAM)
```
7. Shutdown computer and install Hauppauge Colossus 01414 PCI card, power up - Windows 7 will not be able to find drivers for it. If you look in your device manager, you’ll see the card is unrecognized.
8. Install Hauppauge Colossus 01414 PCI Windows 7 driver drivers from the link [above](#drivers-used). Ensure you see the correct card listed under Device Manager/Sound, video and game controllers. There should be two entries:
```
- Colossus Capture Device
- Colossus Encoder Device
```
9. Connect the IR blaster to Colossus card by using the port that looks like a stereo mini jack. The Colossus IR blaster comes with two ends: the larger circular one is the receiver for the Hauppauge remote (we will not use it), the smaller rectangular one is what you tape to the front of the Dish Network VIP 211k. If you haven’t used IR blasters before, the smaller end has a red side and a clear side with a sticky. 
10. <p align="center"><img src="https://github.com/nelinory/WMC7-DishNetwork-Guide/blob/master/Images/ColossusIrBlaster.png" alt="colossus_ir_blaster" width="400"/></p>