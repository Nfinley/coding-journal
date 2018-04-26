# Stackline Dev Onboarding Checklist


## To Download:

- [ ] WeWork app to set up Keycard Access (under account tab)
- [ ] Xcode for Git
- [ ] Browser client of choice
- [ ] Slack Deskptop App (optional, can use web version)
- [ ] IDE of choice (use [VS Code](https://code.visualstudio.com/), [Visual Studio](https://www.visualstudio.com/vs/) or [JetBrains Rider](https://www.jetbrains.com/rider/) for .Net/C# content)
    - [ ] If you use Rider you can use `http://xidea.online` as the license server when setting up
- [ ] Install the current [Node](https://nodejs.org/en/download/) version then downgrade to 8.10:

````bash
    sudo npm cache clean -f
    sudo npm install -g n
    sudo n 8.10
````

- [ ] [.Net Core SDK for mac](https://docs.microsoft.com/en-us/dotnet/core/macos-prerequisites?tabs=netcore2x)
    - [ ] If using VsCode you should also install the `C# for Visual Studio Code (powered by OmniSharp)` extension
- [ ] Once you have access to AWS, generate HTTPS token for cloning (current method used)
- [ ] Download [DBeaver](https://dbeaver.jkiss.org/download/) - Preffered
- [ ] Download [SQL Workbench](https://dev.mysql.com/downloads/workbench/)
- [ ] Download Homebrew via the terminal: 
    ````bash
    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    ````
- [ ] For VPN download `sstp-client` (via the terminal): 

    ````bash
    brew install sstp-client
    ````

- [ ] Install Yarn package manager (for front-end): 

    ````bash 
    brew install yarn 
    ````

## To Setup:

- [ ] Other onboarding items on Onboarding doc
- [ ] Outlook : [Office 365](https://www.office.com/) login - password is `Stackline1234`
- [ ] Slack access (Should have email invite in inbox, otherwise discuss with Ryan Jones)
- [ ] We Work:  Complete profile (from email)
- [ ] AWS Set up/Login (Raj or Abhijeet set up new account)
    - Use US West (origin)
- [ ] VPN (using scripts below or download files in repository)
- [ ] Foundry/Foundry-2 Login (Raj to provide)
- [ ] Atlas/Beacon Login (Raj to provide)
- [ ] Mixpanel dashboard access (Abhijeet or Raj to send invite email): used to track user clicks within Atlas and Beacon
- [ ] Kibana Dasboard: Access through
- [ ] Database Setup: 


## Instructions to run Atlas 

I. Setup the API repository

- [ ] Git clone the `api` repository on AWS (this is the C# .NetCore api interface)
- [ ] Open using IDE of choice (as mentioned above)
- [ ] Follow the [API Repo Setup Instructions](#api-repo-setup-instructions) to prepare the environment
- [ ] Build the `api` project using either the `Api` or `Api(non-build)` config

II. Setup the atlas repository

- [ ] Follow the steps inside of the `beacon` repository on AWS code commit to clone the repository and set up the react application
- [ ] Use the IDE of your choice for the react application

III. Final Steps

- [ ] Run the VPN (using the scripts below)
- [ ] Make sure `api` repository is built with no errors
- [ ] Make sure your atlas repository is running using `yarn run compile`
- [ ] If port forwarding is set up correctly you should be able to hit the url: `https://atlas-localhost.stackline.com/sign_in` and it will load the login screen


### API Repo Setup Instructions

1. Perform the following actions in the terminal:
````bash
mkdir -p ~/wwwroot/wwwroot
cp ./Stackline.Api/wildcard.stackline.pfx ~/wwwroot/
cp ./Stackline.Api/WebIISUrlRewrite.config ~/wwwroot/
cp ./Stackline.Api/appsettings.json ~/wwwroot/
cp ./Stackline.Api/Web.config ~/wwwroot/
cp -r ./Stackline.Api/App_Data ~/wwwroot/ 
````
2. Add the following lines to the /etc/hosts file: 

````bash
sudo vi /etc/hosts 
#Then copy the following lines into the file
127.0.0.1       beacon-localhost.stackline.com
127.0.0.1       atlas-localhost.stackline.com
````

3. Set up port forwarding for 443 to 8443 and 80 to 8080 on localhost: 

````bash
sudo cp ./Stackline.Api/Development_Env_Setup/stackline.local /etc/pf.anchors/`
````
4. Edit the file `/etc/pf.conf` to look like the `pf.conf` file in the Development_Env_Setup folder (referenced below as well)

````bash
scrub-anchor "com.apple/*"
nat-anchor "com.apple/*"
rdr-anchor "com.apple/*"
rdr-anchor "stackline.local"
dummynet-anchor "com.apple/*"
anchor "com.apple/*"
load anchor "com.apple" from "/etc/pf.anchors/com.apple"
load anchor "stackline.local" from "/etc/pf.anchors/stackline.local"
````

5. Run the following command to load the modified pf.conf file: 

````bash
sudo pfctl -ef /etc/pf.conf 
````

### VPN Scripts

- [ ] Save the following three files in your `/etc/ppp/` folder
- [ ] Run `chmod 775 /path/to/thefiles`

### vpn_start.sh

- NOTE: in the vpn_start.sh replace the password with the vpn server password: `Atlas908A1!`

````bash

#!/bin/bash
echo "Connecting to stackline vpn"
sudo /usr/local/sbin/sstpc --log-stderr --cert-warn --user stack-vpn01\\stacklinevpn --password <password> vpn.stackline.com:27000 usepeerdns require-mschap-v2 noauth noipdefault refuse-eap noccp &
echo "Connected to stackline vpn"

````

### vpn_stop.sh

```bash

#!/bin/bash
echo "Disconnecting from stackline vpn"
sudo kill $(ps aux | grep 'sstp' | awk '{print $2}')
echo "Disconnected from stackline vpn"

```

### ip-up
* This adds the subnet to the VPN

```bash

#!/bin/sh
/sbin/route add -net 172.31.0.0/16 -interface ppp0
#/sbin/route add -net 192.168.0.0/16 -interface ppp0

```
