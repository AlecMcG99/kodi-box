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

## Orange Pi setup
If you want to configure kodi yourself, only follow steps 1-4, if you want to import a configuration that I built, follow all these steps
1. Assemble orange pi
2. Insert SD card into other computer and follow the instructions to create a bootable SD card here https://libreelec.tv/downloads/
3. Remove SD card and insert it into the orange pi and turn it on
4. Follow the set up steps in Libreelec wizard, make sure to enable ssh and keep the default username and password, these should be root and libreelec
5. On your other computer, open powershell and run `ssh root@libreelec` and answer yes to any prompts. When prompted for a password type 'libreelec'
6. You are now typing in a remote shell on your orange pi. Run `install2emmc`. This flashes the OS you have on your SD card to the internal storage(eMMC) on your orange pi.
7. Turn off your orange pi and remove your SD card. Your Libreelec/kodi installation is now contained on the internal storage of your orange pi.
8. You now have a working kodi setup! Follow the Configuring kodi section to set up kodi with a skin and add-ons that I have found or feel free to find skins and add-ons yourself

## Configuring Kodi
1. On your other computer, download the 64-bit x86 version of pscp here, look under Alternative binary files to find it: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
2. Move pscp.exe to C:\Users\<your_username>\AppData\Local\Microsoft\WindowsApps or any of the filepaths that are displayed by running `echo $Env:Path` in powershell
3. Download the .kodi config directory
4. Open Powershell and navigate to the directory where you stored the .kodi directory by running `cd <path_to_directory>` For Example, If my .kodi directory were in my downloads folder, I would run `cd C:\Users\asmcg\Downloads\`
5. run the command `pscp -r .kodi root@libreelec:/storage`
6. Restart your orange pi
7. When it boots up again go to settings -> System -> Add-ons and change the settings to look like this if they aren't already ![image](https://github.com/AlecMcG99/kodi-streaming-box/assets/53317718/b43dba91-6e31-4592-aefd-47e365173c29)
8. Go to settings -> Interface -> Skin and click the skin option and select Arctic Horizon 2
    ![image](https://github.com/AlecMcG99/kodi-streaming-box/assets/53317718/3dea19f1-09a9-4457-bbb9-3bfa267b4ee3)
    ![image](https://github.com/AlecMcG99/kodi-streaming-box/assets/53317718/bf458278-912f-41c2-82b0-4ed8bfa85dca)
9. Go to the menu in the top right and select Add-ons ![image](https://github.com/AlecMcG99/kodi-streaming-box/assets/53317718/1ab06c16-7a04-4e79-92a2-af27c2db29c7)
10. Go to running Add-ons, click umbrella and access the menu by clicking left on a d-pad or arrow keys. Make sure it is enabled and then go to manage -> settings
12. Scroll down until you find Trakt, click Authorization then follow the instructions on your other computer
13. Scroll to Accounts(Debrid), under Real-Debrid click Authorization and follow the instructions on your other computer
14. Go back to the Add-ons menu, into the Trakt addon settings, and authorize Trakt again there
15. You should be all set to use kodi with Real-Debrid!

## Further Customization
Here is a breakdown of the add-ons in this setup:
- Skin: Arctic Horizon 2 - makes everything look nice
- Umbrella: Connects to Debrid services
- Cocoscrapers: Umbrella uses this to find torrents
- Mad Titan Sports: Finds live sports


