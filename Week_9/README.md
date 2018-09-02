# Project 9 - Honeypot

Time spent: **8** hours spent in total

> Objective: Setup a honeypot and intercept some attempted attacks in the wild.

## Project Details

- [X] Milestone 0: To the Cloud!
	- I used the Google Cloud Platform for this project (A). I initialized a project and downloaded the GCP SDK with beta commands.

- [X] Milestone 1: Create MHN Admin VM
	- I signed up for a free trail of the Google Compute Engine API. Then, I created an Ubuntu 14.04 VM for the Modern Honeypot Network (MHN) to be controlled from. Finally, I created a firewall rule to allow MHN to communicate with the admin VM.

- [X] Milestone 2: Install the MHN Admin Application
	- I downloaded the MHN Application (https://github.com/RedolentSun/mhn.git) to the VM (via an ssh connection), and installed the application. I used default values (B). Then, I logged into the MHN admin console (C).

- [X] Milestone 3: Create a MHN Honeypot VM
	- I created an Ubuntu 14.04 VM for the Honeypot itself. This was bascially a repeat of Milestone 1.

- [X] Milestone 4: Install the Honeypot Application
	- I ran a script to connect the Honeypot to the MHN admin.
	- $ wget "http://35.202.175.213/api/script/?text=true&script_id=4" -O deploy.sh && \
	sudo bash deploy.sh http://35.202.175.213 NBh3duJG
	- Note that from the command above, 35.202.175.213 was the public IP for the MHN admin.

- [X] Milestone 5: Attack!
	- I logged into a Kali VM, and I ran an NMAP scan against my honeypot. This was just so that I could see what an attack looked like from the admin. I then let the honeypot sit, and I waited. 

## Honeypot

I deployed the "Ubuntu - Dionaea with HTTP" honeypot via the Modern Honeypot Network (MHN) application. I allowed it to run for 16.5 hours before downloading the data. 

## Data Collected

In total, I collected 4,280 attacks. Of these attacks, 3,371 originated from an nmap scan that I ran from a Kali VM. The remaining 909 attacks originated from outside sources. 

## Issues

Encountered issues have been marked with a letter throughout this writeup. These are descriptions for those issues.

(A) It took me a little bit to realize that my school has Google Cloud disabled for school email accounts. I finally realized this, switched to a personal gmail account, and all was good.

(B) The first time I installed this application, I was not able to access the MHN admin console (I just ran the install.sh script). After some troubleshooting, I deleted and recreated the VM. This time, I installed MHN using 
$ sudo -H ./install.sh
and all was good. 

(C) For quite a while, I was not able to access the MHN admin console. Come to find out, it can be chalked up to my lack of familiarity with Google Cloud Platform. I ended up having to edit the settings for the VM to allow HTTP traffic. After I did this, all was good. I assumed that HTTP traffic would have been allowed by default. 

## Notes

I am not sure if this is an issue with MHN (as others using Dionaea did not have this issue), but I was not able to collect any malware payloads. I was only ever able to see the IP that the attack was originating from as well as port and protocol. Others have indicated that they have had this issue as well when using MHN (https://github.com/threatstream/mhn/issues/417). In the future, I would like to try this experiment again without MHN, as I was looking forward to checking out some collected samples. 
