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
> Note: All provided download links are from Hauppauge website. All Hauppauge driver downloads seems to be hosted on amazon.

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