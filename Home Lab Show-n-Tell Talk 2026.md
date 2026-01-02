% Secret Lair Lab  
% Joseph Cathell [kamikazejoe@gmail.com](mailto:kamikazejoe@gmail.com)  
Talk: \[${TALK_URL}](${TALK_URL})  
Repo: \[${REPO_URL}](${REPO_URL})

# Secret Lair Lab

<img src="../../_resources/signal-2025-10-11-111157.jpeg" alt="signal-2025-10-11-111157.jpeg" width="547" height="729" class="jop-noMdConv">

::: notes

:::

# Network Map

<img src="../../_resources/d00e6949d9a71e82bb88e5b7f43d548c.png" alt="d00e6949d9a71e82bb88e5b7f43d548c.png" width="851" height="486" class="jop-noMdConv">

::: notes

:::

# Hardware Rundown

::: notes

:::

## Bandwidth

1 Gbps Fiber from i3 Broadband

::: notes

They offer up to 8 Gbps, but I would have to do a lot of upgrading.

:::

## Switch

Old Avaya Gigabit 48 port switch

::: notes

Got a bunch of these years ago from surplus.  
Probably should be replaced

:::

## Firewall

- Dell R210
- Intel Xeon E3-1240 @ 3.40GHz, 4 cores
- 16GB RAM
- 256 SSD
- OPNSense

::: notes

Works. Gets the job done  
No complaints

:::

## VM Cluster

- 3x Dell R320
- Intel Xeon E5-2430 @ 2.70 GHz, 12 cores
- 32GB RAM
- Proxmox Clustered for HA

::: notes

Scored several of these on craigslist.  
Figured at minimum I'd have spare parts if one failed.  
Thought it would be fun to try and create a VM cluster  
Originally had a convoluted combination of QEMU and custom scripts  
My philosophy being doing things the hardest way possible to learn the most  
Needed to get work done though, so I switched to Proxmox

:::

## Storage NAS

- Old DataDomain 510
- Dual Intel Xeon 5110 @ 1.60GHz, 4 Cores
- 32GB RAM
- 26 TB RAID6 (RAIDZ2)
- Arch Linux and Samba
- Really need to replace

::: notes

Old craigslist purchase.  
Weighs a ton.  
Easily the noisiest thing in the rack.  
Needs a backup solution

:::

## Wifi AP

- TP-Link AC1750
- OpenWRT
- On it's last leg

::: notes

Originally got because Ben West recommended it to me at the time.  
And if you know Ben West, you follow his recommendation for anything WiFi

:::

# Building

- All VMs deployed with Ansible
- Combination of iDRAC and PiKVMs to manage

::: notes

Had to rebuild everything this past year.
Made sure to deploy everything by ansible so I could reproduce it easily
Tried Nix before that, but never got it working how I liked
Got several to the point where not only were systems deployed,
But backups were loaded back in and acounts automatically created.
Unfortunately I don't have those playbooks here to share today.

:::

# Highlights

## The LED Bar

![408722864fc3c59c81d5d9448c2f3fec.png](../../_resources/408722864fc3c59c81d5d9448c2f3fec.png)

::: notes

LED Bar in my server rack.
ESPHome is the firmware
Displays MQTT Messages
Have some weather alerts going to it
As well as status messages sent by ansible playbooks

:::

## The LED Bar

<img src="../../_resources/08923074c40cb1c7796d6905cc368bf9.png" alt="08923074c40cb1c7796d6905cc368bf9.png" width="466" height="390">

::: notes

Came as a kit with Hackerbox #114.
But the parts are easy enought to come by.
Three MAX7219 8x32 Dot Matrix Display Modules
An ESP32. In this case an ESP32-C3 Supermini

:::

## The ON-AIR Light

<img src="../../_resources/image-2025-06-18-131501.jpg" alt="image-2025-06-18-131501.jpg" width="765" height="430" class="jop-noMdConv"> 

::: notes

My girlfriend asked for a light or something to know when I'm in a meeting as not to inturrupt me.
This was my solution.
Turns on when my laptop's mic or camera is in use.

Just found a cheap ON-AIR light-up sign online.
Was about $15
Put in a $10 ESP32
Power the LEDs straight off the ESP
Controlled with Home Assistant and  ESPHome.

:::

# Until...

<img src="../../_resources/image-2025-12-28-202622.png" alt="image-2025-12-28-202622.png" width="358" height="548" class="jop-noMdConv">

::: notes

Last Sunday I came home from a family dinner to find all of my VMs in an "Unknown State"
Turns out I have multiple drive failures across my nodes
I gambled with some refurbished white lable drives, figuring the redundancy would save me
Alas, it did not.
Forunately I have my ansible playbooks archived

:::