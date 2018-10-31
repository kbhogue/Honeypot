# Honeypot
Week 9 Submission

### Honeypot Deployed
I deployed the Modern Honey Network's Dionaea honeypot

### Issues
1. After downloading SDK, my local terminal kept freezing when I attempted to set up the firewall. Eventually, I attempted to run the same commands in the gcloud terminal, and they worked fine. 
2. The git repo we were instructed to download no longer exists, so the "$ sudo git clone https://github.com/RedolentSun/mhn.git" command failed. Instead, I cloned the repo at "https://github.com/threatstream/mhn.git".
3. After setting up the VM, I spent a few days tryng to access the MHN admin console by using the external IP address. I finally discovered that the firewalls were set to block HTTP and HTTPS traffic in the VM instance details. Once I changed the firewalls to allow HTTP and HTTPS traffic, I was able to access the MHN admin console and deploy my honeypot. 
4. The commands given to export the json were also outdated. I ended up running the following commands in my local terminal to export the json file. 
$ gcloud config set core/project disco-portal-220520
$ gcloud compute ssh mhn-admin --zone="us-central1-c" --command="mongoexport --db mnemosyne --collection session > session.json"
$ gcloud compute scp mhn-admin:session.json ./session.json

### Summary of Data
I let the honeypot run for about 20 hours. In that time, I recorded 2614 attacks to my Dionaea honeypot. The attacks came from various countries, but about half of them came from within the US. Most attacks used pcap protocol, but other protocols such as SipSession and SipCall were also detected. Course and destination ports varied from each attack. 
![](honeypot.gif)

### Unresolved Questions
None
