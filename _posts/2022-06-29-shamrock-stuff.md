---
title: "Shamrock Stuff"
layout: post
---

![3 Dell PowerEdge r710 servers, laid out open on the floor](/assets/img/2022-06-30-shamrock-floor.jpg)

Right now [Shamrock Cluster](https://shamrock.systems/), my own personal "cloud" service, is completely offline. It's
pretty obvious why though, right? All the hardware is open on the floor! There's a good reason for this though, let me
preview a bit of what I'm working on:


- **I'm getting rid of switches!** All the Dell PowerEdge r710s are getting wired together directly using their
  NICs! [Proxmox SDN](https://pve.proxmox.com/wiki/Software_Defined_Network) seems like an appealing solution for both
  increasing local bandwidth on hyper-converged setups like mine, and providing a good platform for virtualized HA
  network appliances like routers (OPNsense in the future maybe?).
- **I'm making the RAM configuration less bad!** Previously the cluster ran some really lopsided machines. One rack
  would have 16 threads while the other two would have 24. And we would have 128GB, 130+ GB, and 72 GB configurations of
  memory. Not that easy to configure and balance stuff when your hypervisors themselves aren't balanced. Right now I'm
  looking into trading some memory with friends so that I can satisfy the Dell Memory Optimizer, to balance at least 96
  GB to each rack.
- **I'm changing up networking!** The reality is that on-premises clusters, especially those hosted on home networks,
  *will* go down at some point. That's why I'm going to change up my networking
  using [Tailsacle](https://tailscale.com/) in such a way, so that even if my on-premises system goes down, a few
  lightweight VMs on the cloud will at least show some decent error messages and status pages before things come back
  online.

Hopefully I can get through this soon, and before the Purdue move-in date!