# Nexpose / Nessus Vulnerability Scanner (Highly Recommend)

- Nexpose: http://www.rapid7.com/products/nexpose
- Nessus: [Nessus Vulnerability Scanner: Network Security Solution | Tenable®](https://www.tenable.com/products/nessus)
- Burp Suite: http://portswigger.net/burp/
- OWASPs ZAP scanner: http://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project

---
### Automated Web Application Scanners

- IBM AppScan: [IBM Products](https://www.ibm.com/products)
- HP Web compURI: [Laptop Computers, Desktops, Printers, Ink & Toner | HP® Official Site](https://www.hp.com/us-en/home.html)

---
## High level tools list additional to Kali:

- Discover Scripts (formally Backtrack Scripts) 

- SMBexec 

- Veil 

- WCE 

- Mimikatz 

- Password Lists 

- Burp 

- PeepingTom

- gnmap.pl 

- PowerSploit 

- Responder 
  
- BeEF 
  
- Firefox 
  
	- Web Developer Add-on 
	- Tamper Data 
	- Foxy Proxy 
	- User Agent Switcher

----
- You can download the Kali distro from http://www.kali.org/downloads/. I highly recommend you download the VMware image and download VMPlayer/VirtualBox. It is gz compressed and tar archived, so make sure to extract them first and load the vmx file.

### Once Your Kali VM is Up and Running:

1. Login in with the username root and the default password ...

2. Open a Terminal

3. Change Password
   
	1. Always important to change the root password, especially if you enable SSH services.
	2. passwd
	   
4. Update Image with the Command:

```bash
apt-get upgrade
```

```bash
apt-get dist-upgrade
```


5. Setup database for Metasploit:
   
	1. This is to configure Metasploit to use a database for stored results and indexing the modules.

```bash
service postgresql start
```

```bash
service Metasploit start
```

6. Optional for Metasploit - Enable Logging
   
	1. I keep this as an optional since logs get pretty big, but you have the ability to log every command and result from Metasploit’s ==Command Line Interface (CLI).== This becomes very useful for bulk attack/queries or if your client requires these logs.
	2. echo `“spool/root/msf_console.log” >/root/.msf4/msfconsole.rc`
	3. Logs will be stored at/root/msf_console.log

---
### Install Discover Scripts (originally called Backtrack-scripts)
	
	1.  Discover is used for Passive Enumeration
	2. cd/opt/
	3. git clone https://github.com/leebaird/discover.git 
	4. cd discover/
	5. ./setup.sh

---
### Install Smbexec
 
1. Smbexec will be used to grab hashes out of the Domain Controller and reverse shells
2. cd/opt/ 
3. git clone https://github.com/brav0hax/smbexec.git 
4. cd smbexec 
5. ./install.sh 
   
	1. Choose number 1
	   
6. Install to/opt 
7. ./install.sh 
	1.  Choose number 4

---
### Install Veil 

1. Veil will be used to create python based Meterpreter executable 
2. cd/opt/ 
3. git clone https://github.com/veil-evasion/Veil.git 
4. cd ./Veil/setup 
5. ./setup.sh

---
### Download WCE 

1. Windows Credential Editor (WCE) will be used to pull passwords from memory 
2. cd ~/Desktop 
3. wget http://www.ampliasecurity.com/research/wce_v1_41beta_universal.zip 
4. unzip -d ./wce wce_v1_41beta_universal.zip

---
### Download Mimikatz 

1. Mimikatz will be used to pull passwords from memory 
2. cd ~/Desktop 
3. wget http://blog.gentilkiwi.com/downloads/mimikatz_trunk.zip 
4. unzip -d./mimikatz mimikatz_trunk.zip

---
### Saving Custom Password Lists 

1. Password lists for cracking hashes 
2. cd ~/Desktop 
3. mkdir ./password_list && cd ./password_list 
4. Download large password list via browser and save to ./password_list: https://mega.co.nz/#!3VZiEJ4L!TitrTiiwygI2I_7V2bRWBH6rOqlcJ14tSjss2qR5dqo 
5. gzip -d crackstation-human-only.txt.gz 
6. wget http://downloads.skullsecurity.org/passwords/rockyou.txt.bz2 
7. bzip2 -d rockyou.txt.bz2

---
### Setting up Peepingtom

1. Peepingtom will be used to take snapshots of webpages 
2. cd/opt/ 
3. git clone https://bitbucket.org/LaNMaSteR53/peepingtom.git 
4. cd ./peepingtom/ 
5. wget https://gist.github.com/nopslider/5984316/raw/423b02c53d225fe8dfb4e2df9a20bc800cc7 
6. wget https://phantomjs.googlecode.com/files/phantomjs1.9.2-linux-i686.tar.bz2 
7. tar xvjf phantomjs-1.9.2-linux-i686.tar.bz2 
8. cp ./phantomjs-1.9.2-linux-i686/bin/phantomjs 

---
### Adding Nmap script 

1. The banner-plus.nse will be used for quicker scanning and smarter identification 
2. cd/usr/share/nmap/scripts/ 
3. wget https://raw.github.com/hdm/scan-tools/master/nse/banner-plus.nse

---
### Installing PowerSploit

1. PowerSploit are PowerShell scripts for post exploitation 
2. cd/opt/ 
3. git clone https://github.com/mattifestation/PowerSploit.git 
4. cd PowerSploit 
5. wget https://raw.github.com/obscuresec/random/master/StartListener.py 
6. wget https://raw.github.com/darkoperator/powershell_scripts/master/ps_encoder.py

---
### Installing Responder

1. Responder will be used to gain NTLM challenge/response hashes 
2. cd/opt/ 
3. git clone https://github.com/SpiderLabs/Responder.git

---
### Installing Social Engineering Toolkit (don’t need to re-install on Kali) (SET) 

1. SET will be used for the social engineering campaigns 
2. cd/opt/ 
3. git clone https://github.com/trustedsec/social-engineer-toolkit
4. cd set 
5. ./setup.py install

---
### Install bypassuac 

1. Will be used to bypass UAC in the post exploitation sections
2. cd/opt/ 
3. wget http://www.secmaniac.com/files/bypassuac.zip 
4. unzip bypassuac.zip 
5. cp bypassuac/bypassuac.rb/opt/metasploit/apps/pro/msf3/scripts/meterpreter/ 
6. mv bypassuac/uac//opt/metasploit/apps/pro/msf3/data/exploits/

---
### Installing BeEF 

1. BeEF will be used as an cross-site scripting attack framework 
2. apt-get install beef-xss

---
### Installing Fuzzing Lists (SecLists) 

1. These are scripts to use with Burp to fuzz parameters 
2. cd/opt/ 
3. git clone https://github.com/danielmiessler/SecLists.git

---
### Installing Firefox Addons 

1. Web Developer Add-on: https://addons.mozilla.org/en-US/firefox/addon/web-developer/ 
2. Tamper Data: https://addons.mozilla.org/en-US/firefox/addon/tamper-data/ 
3. Foxy Proxy: https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/ 
4. User Agent Switcher: https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/

---
### Windows VM HOST

##### High level tools list addition to Windows: 

1. HxD (Hex Editor) 
2. Evade (Used for AV Evasion) 
3. Hyperion (Used for AV Evasion) 
4. Metasploit 
5. Nexpose/Nessus 
	1. nessus key: 3e10d4dbe3b4e95e8114e4405f46832ee10a595a
6. Nmap 
7. oclHashcat 
8. Evil Foca 
9. Cain and Abel 
10. Burp Suite Pro 
11. Nishang 
12. PowerSploit 
    
13. Firefox (Add-ons) 
	1. Web Developer Add-on 
	2. Tamper Data 
	3. Foxy Proxy 
	4. User Agent Switcher

---
###  Setting up Windows

1. There isn’t anything special that I setup on Windows, but usually I’ll install the following. 
2. HxD http://mh-nexus.de/en/hxd/ 
3. Evade https://github.com/govolution/avet
4. Hyperion http://www.nullsecurity.net/tools/binary.html 
   
	1. Download/install a Windows Compiler http://sourceforge.net/projects/mingw/ 
	2. Run “make” in the extracted Hyperion folder and you should have the binary.
	   
5. Download and install Metasploit http://www.Metasploit.com/
6. Download and install either Nessus or Nexpose 
	1. If you are buying your own software, you should probably look into Nessus as it is much cheaper, but both work well
	   
7. Download and install nmap http://nmap.org/download.html 
8. Download and install oclHashcat http://hashcat.net/oclhashcat/#downloadlatest 
9. Download and install evil foca http://www.informatica64.com/evilfoca/
10. Download and install Cain and Abel http://www.oxid.it/cain.html
11. BURP http://portswigger.net/burp/download.html
12. Download and extract Nishang: https://code.google.com/p/nishang/downloads/list
13. Download and extract PowerSploit: https://github.com/PowerShellMafia/PowerSploit
    
14. Installing Firefox Addons
    
	1. Web Developer Add-on: https://addons.mozilla.org/en-US/firefox/addon/web-developer/
	2. Tamper Data: https://addons.mozilla.org/en-US/firefox/addon/tamper-data/ 
	3. Foxy Proxy: https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/ 
	4. User Agent Switcher: https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/

---
