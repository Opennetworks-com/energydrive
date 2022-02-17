# ED-iot
Energy Drive - IoT Device - Loadout

Suggested for Ubuntu Core:
https://ubuntu.com/download/raspberry-pi/thank-you?version=20&architecture=core-20-arm64+raspi

Ubuntu Core is Snap containet architected. To Run Java and Python, you'll need to install dependancies to support
this runtime environment first. I've included buildouts based on this updated support article:
https://ubuntu.com/blog/how-to-snap-introducing-classic-confinement


This is a setup script to automate the setup and provisioning of Ubuntu servers. It does the following:
* Adds a new user account with sudo access
* Adds a public ssh key for the new user account
* Disables password authentication to the server
* Deny root login to the server
* Setup Uncomplicated Firewall
* Create Swap file based on machine's installed memory
* Setup the timezone for the server (Default to "Africa/Johannesburg")
* Install Network 
* Download and install dependancies
* Bind and add to Core IoT for Energy Drive
* Creates Heartbeat System and sends device statistics to BigQuery / Fulcrum
* Most Loaout set are cloned from https://github.com/tim0n3/AutoPai

# Installation
SSH into your server and install git if it is not installed:
```bash
sudo apt-get update
sudo apt-get install git
```

Clone this repository into your home directory:
```bash
cd ~
git clone https://github.com/Opennetworks-com/energrydrive.git
```

Run the setup script
```bash
cd energydrive
bash setup.sh
```

# Setup prompts
When the setup script is run, you will be prompted to enter the username and password of the new user account. 

Following that, you will then be prompted to add a public ssh key (which should be from your local machine) for the new account. To generate an ssh key from your local machine:
```bash
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub
```

Finally, you will be prompted to specify a [timezone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) for the server. It will be set to 'Africa/Johannesburg' if you do not specify a value.
