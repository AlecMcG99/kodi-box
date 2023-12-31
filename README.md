# kodi-streaming-box
Files and instructions for setting up a LibreElec Kodi streaming box with the Arctic Horizon 2 skin, Real Debrid and Trakt

## Hardware Requirements
- Single Board Computer (I used the orange pi 3 lts) https://www.amazon.com/dp/B09TQZH4GJ/?coliid=I1RXGT6Y8PQ8GU&colid=11DNH89NLYSHV&psc=1&ref_=list_c_wl_lv_ov_lig_dp_it
- Sd Card https://www.amazon.com/dp/B0B7NXBM6P/?coliid=IGJJ0WJ89QH97&colid=11DNH89NLYSHV&psc=1&ref_=list_c_wl_lv_ov_lig_dp_it
- HDMI Cable https://www.amazon.com/dp/B074FCPFV8/?coliid=I2KW8VJ5O1ER0K&colid=11DNH89NLYSHV&psc=1&ref_=list_c_wl_lv_ov_lig_dp_it
- Ethernet Cable (Optional but highly recommended if you have the ability to hardwire your internet connection) https://www.amazon.com/dp/B08PKYN463/?coliid=IG38IRTAZFRPF&colid=11DNH89NLYSHV&psc=1&ref_=list_c_wl_lv_ov_lig_dp_it
- Sd card reader (Optional, required if your computer doesn't have a sd card slot) https://www.amazon.com/Reader-Beikell-Connector-Memory-Adapter/dp/B0BGNZGDTC/ref=sr_1_3?crid=3PB5AMSWIY5Q6&keywords=sd+card+reader&qid=1696803817&sprefix=%2Caps%2C105&sr=8-3
- Usb Remote (Optional, feel free to find any 2.4 Ghz usb remote that works with linux) https://www.amazon.com/dp/B07D2BG6R5/?coliid=I14MYI66BE1GA5&colid=11DNH89NLYSHV&psc=1&ref_=list_c_wl_lv_ov_lig_dp_it

## External account setup
1. Sign up for an account at https://real-debrid.com/ and pay for any amount of days. This will allow you to search cached torrents on real debrid 
2. Sign up for a trakt.tv account here https://trakt.tv. this will keep track of what shows/movies you've watched and give you recommendations

## Orange Pi Setup (Plug and Play Image)
1. Assemble orange pi (The heatsink goes on the chip labeled H6)
2. Download the source code zip file for release v1.1.0 and unzip it
3. Insert the SD card into your computer and run usbImager.exe from the unzipped folder
4. Using the three dots, select the Libreelec-kodi-orange-pi-3-lts.img.gz file and use the drop down to select your SD card and click write <img src="images/7.png" height=200 align="top"/>
5. You now have a working kodi setup! Follow the Configuring Add-ons section to connect the add-ons to your Real-Debrid and Trakt accounts
   
## Orange Pi Setup (LibreElec Image)
If you want to configure kodi yourself, only follow steps 1-4, if you want to import a configuration that I built, follow all these steps
1. Assemble orange pi (The heatsink goes on the chip labeled H6)
2. Insert SD card into other computer and follow the instructions to create a bootable SD card here https://libreelec.tv/downloads/
3. Remove SD card and insert it into the orange pi and turn it on
4. Follow the set up steps in Libreelec wizard, make sure to enable ssh and keep the default username and password, these should be root and libreelec
5. On your other computer, open powershell and run `ssh root@libreelec` and answer yes to any prompts. When prompted for a password type 'libreelec'
6. You are now typing in a remote shell on your orange pi. Run `install2emmc`. This flashes the OS you have on your SD card to the internal storage(eMMC) on your orange pi.
7. Turn off your orange pi and remove your SD card. Your Libreelec/kodi installation is now contained on the internal storage of your orange pi.
8. You now have a working kodi setup! Follow the rest of this section to install the skin and add-ons that I've put together or feel free to find your own setup that works for you
9. On your other computer, download the 64-bit x86 version of pscp here, look under Alternative binary files to find it: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
10. Move pscp.exe to C:\Users\<your_username>\AppData\Local\Microsoft\WindowsApps or any of the filepaths that are displayed by running `echo $Env:Path` in powershell
11. Download the v1.0.0 from the release section of this repository and unzip the .kodi folder. Make sure it's named .kodi
12. Open Powershell and navigate to the directory where you stored the .kodi directory by running `cd <path_to_directory>` For Example, If my .kodi directory were in my downloads folder, I would run `cd C:\Users\asmcg\Downloads\`
13. run `pscp -r .kodi root@libreelec:/storage` If it prompts you for a password, type 'libreelec',
13a. If you get this error:<img src="images/6.png" height=200 align="top"/> 

     Delete the file C:/Users/<username>/.ssh/known_hosts and rerun `pscp -r .kodi root@libreelec:/storage`

14. Restart your orange pi

## Configuring Add-ons
1. In your kodi installation go to settings -> System -> Add-ons and change the settings to look like this if they aren't already  <img src="images/3.png" height=300/>
2. Go to settings -> Interface -> Skin and click the skin option and select Arctic Horizon 2
     <img src="images/1.png" height=300/>
     <img src="images/2.png" height=300/>
3. Go to the menu in the top right and select Add-ons  <img src="images/4.png" height=300 align="top"/>
4. Go to running Add-ons, click umbrella and access the menu by clicking left on the d-pad or arrow keys. Make sure it is enabled and then go to manage -> settings  <img src="images/5.png" height=300 align="top"/>
5. Scroll down until you find Trakt, click Authorization then follow the instructions on your other computer
6. Scroll to Accounts(Debrid), under Real-Debrid click Authorization and follow the instructions on your other computer
7. Go back to the Add-ons menu, into the Trakt addon settings, and authorize Trakt again there
8. You should be all set to use kodi with Real-Debrid!

## Further Customization
Here is a breakdown of the add-ons in this setup:
- Skin: Arctic Horizon 2 - makes everything look nice
- Umbrella: Connects to Debrid services
- Cocoscrapers: Umbrella uses this to find torrents
- Mad Titan Sports: Finds live sports
- tinc: VPN


