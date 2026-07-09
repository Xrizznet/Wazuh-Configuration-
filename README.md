# Wazuh-Configuration
## Configuring Wazuh All in One Troubleshooting and notes

Following up on my previous project in the process of building my home lab: Setting up Wazuh.

## Installation Process
As you see in the first portion of my project prepping my virtual machine for Wazuh the issue was that the VDI itself was too small and I was using the incorrect vesion of ubuntu for the AIO manager.
Never the less the proces of: Virtual-Machine-Storage-Expansion-Proces.I proceeded with the installtion of Wazuh and recieved a alert that I dont have enough storage in the system. I confirmed this error, exapanded the storage device, and proceeded with the installation.

<img width="1400" height="831" alt="Screenshot 2026-07-05 220443" src="https://github.com/user-attachments/assets/b4afe342-eaec-427a-9518-e360add51156" />

<img width="1569" height="1077" alt="Screenshot 2026-07-05 220951" src="https://github.com/user-attachments/assets/9b8329a5-33d7-400d-b745-5386cef8fed7" />

<img width="1460" height="1066" alt="Screenshot 2026-07-05 225141" src="https://github.com/user-attachments/assets/d61d9d97-c296-419d-acb9-29959a4c6126" />

## Issue 1: Wazuh Credentials Login Failed
I was excited that the installation finally worked . I was wrong , when I tried logging into the dash board the admin credentials provided did not work. I'm positive the credentials were entered correctly. 

<img width="1384" height="1049" alt="Screenshot 2026-07-05 225920" src="https://github.com/user-attachments/assets/b625a175-57c0-43d8-af2b-f0c7418de881" />

My first instinct was to update the system and retry the site. Which did not fix the issue and I not think was a bad decision because maybe the cached credentials were changed/ wiped when the update occured. 

<img width="1538" height="637" alt="Screenshot 2026-07-05 233059" src="https://github.com/user-attachments/assets/0aa77db5-6438-4f93-b4a6-e7d9b3968f65" />

<img width="1470" height="914" alt="Screenshot 2026-07-05 233844" src="https://github.com/user-attachments/assets/706d1f27-8871-423c-afef-a363f63d3705" />

# Issue 2: Wazuh Dashboard 
After I completed the update the dashboard would not load back up in the browser: I kept getting error: Unable to connect. Before I panicked I checked to see if I could ping the website, I could. 

<img width="1477" height="859" alt="Screenshot 2026-07-05 235821" src="https://github.com/user-attachments/assets/e9fc0242-1ad4-4e7b-b855-376ecc8b2c7e" />

# Checklist: 
- Check Services running
- Ports listening correspond 
- Check firewall rules inbound/outbound

#  Services and Ports
All services were running I checked the Indexer and Dashboard.  I checked them one by one though I did not screenshot each result. 

<img width="1202" height="883" alt="Screenshot 2026-07-06 203548" src="https://github.com/user-attachments/assets/529d82df-34d0-4268-80da-0835cf0ef48e" />

<img width="1337" height="837" alt="Screenshot 2026-07-06 193946" src="https://github.com/user-attachments/assets/2dac5da8-68f0-40bd-be0e-b2bf5f06e9f7" />

# Firewall 
Results confirmed the wazuh manager services were running and on ports 1514, 1515. I tested if the site would load without SSL using  then SSL , site still would not load and generated the same error message.  

 ```bash
sudo curl -k http://127.0.0.1:443
```

Seeing the return output that the firewall is skipping the rule so port 443 is already allowing incoming traffic on port 443. 

## Final decision

After numerous attempts of trying to fix the issuesI decided to just create another VM and restart the process of configuring  Wazuh on my network. I mad some changes this time around instead of using Ubuntu 22.04 I upgraded to 24.04. I also changed my GUI from XFCE to MATE, I felt its interface was better and already included platforms like firefox. It was a long journey but Wazuh manager has officially been set up. 

<img width="644" height="761" alt="Screenshot 2026-07-09 035827" src="https://github.com/user-attachments/assets/2d2db229-e923-4d4d-b69c-a7296791f2be" />












