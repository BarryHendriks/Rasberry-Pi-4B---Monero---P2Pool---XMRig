# Rasberry-Pi-4B---Monero---P2Pool---XMRig

Auto installer script to install Monero and XMRig on Rasberry Pi 4B

Master installer script (single file, interactive, prompts before destructive actions)
Save this file as ~/xmr-mining-scripts/master_installer.sh, make it executable, then run it from the pi user. 

It will:

update the system and install required packages

prompt to confirm the USB device (defaults to /dev/sda)

partition, format as ext4, label MoneroDB, mount and add fstab entry

create working directories

download and install Monero CLI and build XMRig

create config, systemd units, watchdog and start/enable services

1. You need to use Rasberry Pi imager software to create the latest 64 bit OS image on a 16 Gb SD card and 8Gb memory
   Power up the Rasberry Pi to ensure it is running
2. You need a usb3 stick/drive greater than 128Gb - the current full Monero Blockchain Database is already at 240 Gb and growing DAILY!
3. The usb stick/drive must be mounted on the bottom left blue usb3 socket on the Rasberry Pi for this auto installer and configuration script to work.
4.  USB will be formatted as ext4, labeled as MoneroDB, and mounted at /media/pi/MoneroDB automatically once you run the master_installer script
5. Create a directory on your PI:
   mkdir -p ~/xmr-mining-scripts
6. Copy the "master_installer.sh" file from GitHub repository to your PI:
     wget https://github.com/BarryHendriks/Rasberry-Pi-4B---Monero---P2Pool---XMRig/master_installer.sh ~/xmr-mining-scripts/master_installer.sh
7.  # Fix Windows line endings if needed
     sudo apt update && sudo apt install -y dos2unix
     dos2unix ~/xmr-mining-scripts/master_installer.sh
8. You need to change the name of your XMRig miner and your Monero wallet at the top of the first few lines of the script.
  Edit the file with nano:
    sudo nano ~/xmr-mining-scripts/master_installer.sh
9. How to run the installer script
    SSH into the Pi:
    ssh pi@raspiminer.local      #Change raspiminer.local to YOUR PI installation name
10.  Quick safety and debugging tips - Always inspect script contents before running:
  less ~/xmr-mining-scripts/prep_usb_monero.sh
# Inspect the top and bottom lines to ensure file looks correct
  sed -n '1,120p' ~/xmr-mining-scripts/master_installer.sh
  sed -n '$(( $(wc -l < ~/xmr-mining-scripts/master_installer.sh) - 40 )),$ p' ~/xmr-mining-scripts/master_installer.sh
10.  Make executable to run (after inspection)
    chmod +x ~/xmr-mining-scripts/master_installer.sh
    Use bash -x when debugging a script to see every command as it runs.
11.  Run the script (it will prompt before any destructive actions):
    cd ~/xmr-mining-scripts
    ./master_installer.sh


    
