This directory contains ami-creator kickstart configs used to create
cloud images for RPM-based distros.  In general, the process is:

* git clone https://github.com/eucalyptus/ami-creator.git
* git clone https://github.com/eucalyptus/image-configs.git
* cd image-configs/ami-creator
* mkdir -p f17/tmp

'''
python ../../ami-creator/ami_creator/ami_creator.py -d -e -m \
  -c ks-fedora17.cfg \
  --cache f17/cache \
  --tmp   f17/tmp \
  --logfile f17.log
'''

This creates an ext3 filesystem image and extracts the kernel and
ramdisk into the current directory.  The '-m' option creates udev
configuration to map 'sd' device names to 'xvd' for Xen
compatibility.  For EL 6.x, you also should specify --xvd-offset
to handle differences in the kernel's device enumeration.

