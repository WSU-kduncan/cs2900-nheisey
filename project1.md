# Project 1

## Part 1 - Building VMs

- Guest VM used: Ubuntu Linux
- VMM (virtual machine manager / software): VirtualBox

### Setting up a Ubuntu VM on a Windows 10 host

- **NOTE** - think next semester, you'll take a class that needs familarity with virtual machines.  Give yourself the gift of good documentation

1. Downloaded ISO from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
    - Chose the Desktop ISO to have access to a GUI interface (instead of server where terminal only)
    - Choosing the Desktop edition also allows running of a web browser.  This VM could then be used to demo effects of networking settings by playing with web page access
2. Install VirtualBox for [Windows hosts](https://download.virtualbox.org/virtualbox/6.1.26/VirtualBox-6.1.26-145957-Win.exe)
3. Create a new Virtual Machine - basically, determine the RAM and disk space the virtual machine will be allocated
    - How much disk space?  Fixed or flex?
    10.0gb Fixed
    - How much RAM?  What about your host?
    Ram for vm: 4.6 gb My host pc has 16gb
    - 3D acceleration?  What performance do you need out of your VM?  Do you even have GPU resources to make this really worthwhile?
    3D Acceleration is turned on, I have a RTX 3060 so I have plenty of resources for this
    - Guest Additions - what are you loosing without it, what would you gain with it, and do you want it?
    I have guest additions enabled because it just seems to add many quality of life features when interacting between the Host OS and the Guest OS
4. Install an OS to the Virtual Machine
    - How to specify which ISO is the install ISO
    With the case of the Ubuntu OS I installed it was the only iso in my downloads folder and it had the name of the OS I was installing.
    - Maybe (for your notes) any installation tips / tricks you did
        - I simply went with most of the default settings when setting up this VM it was simple enough and served the purpose I needed it to.
    - How to detach install ISO once done
        - Mine automatically did this. If it doesn't you need to go to the storage settings on your VM and find where you put the ISO on the controller IDE and right click it and hit remove from virtual disk

## Part 2 - Exploring Virtualization

### Exploring Host Disk Usage
1. Describe where your Guest OS is saved and how much space it takes up
My guest OS is saved in the default VirtualBox VMs folder automatically created on my Host OS, it takes up 10.0gb currently
    - From your configuration above, is this going to expand?
    Not unless I manually expand it's memory.
2. Can you directly access your Guest files from the virtual machine image folder?  Why or why not?
Not by default but if I go into the devices tab on VirtualBox and click on the shared folders option choosing which folders I'd like to manually share will allow me do to this.
3. Explore the sizes of creating "snapshots" vs. templates / clone.  What do each of these achieve?

Snapshots essentially are like a save point for your VM. The virtual disk image is about 4mb while the actual sav file is 743mb. The snapshot will increase in size with more changes you make to the disk.

### Exploring Guest Networking

- **NOTE** - assume standard out of box networking configuration, that is to say NAT networking
- Explain your approximate networking configuration for your Host - we talked about the home standard of:
    - modem from ISP, assigns public IP
    - router provides DHCP private network.  Devices are connected to your router, which is your gateway
    - your network requests to sites are routed through your router, which plugs in your public address, requests info from the world, gets the info back, then passes the request back to the device that made it (NAT - Network Address Translation)
    The network configuration for my host is NAT
- Explain the network configuration for your Guest
    - Does your guest have a network accessible address?  For example, can other devices connected to your router get to it?
        - The usual answer is no, so how is your Guest getting network access?
Currently the network configuration is NAT which was the default setting.
## Part 3 - Networking with Style

- Pick a networking method besides NAT, and see what it does.
- Document the networking configuration you choose.  
- In class, we explored bridged & host-only networking, and demonstrated the effects of each of these.
- If I were writing this up, I would likely use the example where I installed a web server and played with accessing it from the different IP configured on my host and guest