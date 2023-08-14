# Single_GPU_Passthrough_Nvidia_GTX_1070
Description: Single GPU passthrough for Nvidia GTX 1070 on Ubuntu 22.04

Specs:
1.	Nvidia GeForce GTX 1070
2.	Intel core i7 7700K

Steps: 
1.	Follow steps 1-6 on the Gitlab link below
  a.	https://gitlab.com/risingprismtv/single-gpu-passthrough/-/wikis/1)-Preparations
2.  Create a backup of the GPU vBios with Nvflash while on Ubuntu Live CD
3.  Patch vBios with this GitHub link: https://github.com/Matoking/NVIDIA-vBIOS-VFIO-Patcher

Directory structure:
```
.
└── Computer/
    └── etc/
        ├── libvirt
        ├── kvm.conf
        └── qemu/
            └── hooks/
                └── qemu.d/
                    └── win11/
                        ├── prepare/
                        │   └── begin/
                        │       └── start.sh
                        └── release/
                            └── end/
                                └── revert.sh
```

Notes:
1.	Must stop all programs associated with the Nvidia graphics card
  a.	This will allow you to unload the drivers and unbind the graphics card
2.  Run the start.sh hook multiple times in the terminal via ssh to make sure the graphics card is unloaded
3.  Start the virtual machine with "virsh start win11"
4.  Stopping the virtual machine with "virsh shutdown win11" will restore gnome desktop


