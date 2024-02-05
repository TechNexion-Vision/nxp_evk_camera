# NXP i.MX 8M Plus Camera Driver

[![p3](https://github.com/TechNexion-Vision/imx8_evk_tevi/assets/57210123/ad8c94e7-8a32-49e8-ac15-f6788125d215)](https://www.technexion.com/products/embedded-vision/)


[![Producer: Technexion](https://img.shields.io/badge/Producer-Technexion-blue.svg)](https://www.technexion.com)
[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
<br/><br/>
## Overview
Driver has been developed by TechNexion as an initiative in order to bootup Technexion MIPI-CSI2 cameras for NXP 8MPLUSLPD4-EVK board with Yocto 4.0 and kernel L5.15.71_2.2.2_MX8MP
## Prerequisites
+ **NXP i.MX 8M Plus EVK**： [8MPLUSLPD4-EVK](https://www.nxp.com/design/design-center/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-plus-applications-processor:8MPLUSLPD4-EVK)
+ **camera + MINI-SAS Cable**： [camera with NXP EVK](https://www.technexion.com/?s=NXP+i.MX8+EVK&post_type=product)<br/>
Prepare adapter board and cable for connect to EVK board.<br/>
        <image src="https://github.com/TechNexion-Vision/imx8_evk_tevi/assets/57210123/8a22ccf3-98b3-489b-95e0-d9f52171e25a"  width="360">
+ **Yocto demo image** <br/>
There are 3 options to get an image, we suggest using first one is the most easy way.<br/>
  1. Using TechNexion's Prebuilt demo image, which contains the required device tree blobs and camera driver.<br/>
      It can be available for download via TechNexion's server： [Image Download Link](https://download.technexion.com/demo_software/EVK/NXP/)<br/>
    1. If you want to build a Yocto Project image by yourself, TechNexion BSP release providing support NXP i.mx series processors：<br/>
        [Fetch Yocto source](https://github.com/TechNexion/tn-imx-yocto-manifest/tree/kirkstone_5.15.y-stable)<br/>
        [Build Yocto](https://github.com/TechNexion/tn-imx-yocto-manifest/tree/hardknott_5.10.y-next#for-nxp-imx8mp-evk-with-technexion-tevi-and-vizionlink-camera-support)<br/>
    1. You can following the NXP's requirements for Yocto Project BSP： [i.MX Yocto Project User's Guide](https://www.nxp.com/docs/en/user-guide/IMX_YOCTO_PROJECT_USERS_GUIDE.pdf)<br/>
+ **SD Card** <br/>
SD card capacity must be > 8GB and then Flash image to SD card.
    - Under Windows flash tool： [balena etcher](https://www.balena.io/etcher/)
    - Under Linux flash tool： [bmap-tools](https://github.com/intel/bmap-tools)<br/>

> [!TIP]
> Ensure the boot mode is configured as **boot from SD card**. <br/>
> Following this page to boot up： [getting-started-with-the-i-mx-8m-plus-evk:GS-iMX-8M-Plus-EVK](https://www.nxp.com/document/guide/getting-started-with-the-i-mx-8m-plus-evk:GS-iMX-8M-Plus-EVK)


## Driver Installation instructions
  If using TechNexion's Prebuilt demo image or build form TechNexion BSP release, it's already installed so you can skip this topic.<br/><br/>
  **1. Download the camera driver and device tree blobs.**
  ```
  $ git clone git@github.com:TechNexion-Vision/imx8_evk_tevi.git
  $ cd imx8_evk_camera/
  ~/imx8_evk_camera$ git checkout tn-imx_5.15.71_2.2.0-stable
  ```
  **2.  Copy to your kernel source code.**
  ```
  ~/imx8_evk_camera$ mv -r driver/media/i2c/tevs/ <fatch_kernel_folder>/driver/media/i2c/
  ~/imx8_evk_camera$ mv arch/arm64/boot/dts/freescale/imx8mp-evk-tevs.dts <fatch_kernel_folder>/arch/arm64/boot/dts/freescale/
  ```
  **3.  Modify makefile to add driver**
  ```
  $ cd <fatch_kernel_folder>/driver/media/i2c/
  ~/<fatch_kernel_folder>/driver/media/i2c/$ vi Makefile
  ```
  Add this line in Makefile.
  ```
  obj-$(CONFIG_VIDEO_TEVS) += tevs/
  ```
  > [!NOTE]
  > you can refer to [linux-tn-imx/drivers/media/i2c/Makefile](https://github.com/TechNexion/linux-tn-imx/blob/tn-imx_5.15.71_2.2.0-next/drivers/media/i2c/Makefile)
  
  Modify Kconfig to add camera config
  ```
  ~/<fatch_kernel_folder>/driver/media/i2c/$ vi Kconfig
  ```
  Add this part under "Camera sensor devices" menu in Kconfig.
  ```
  config VIDEO_TEVS
    tristate "TechNexion TEVS sensor support"
    depends on OF
    depends on GPIOLIB && VIDEO_V4L2 && I2C && VIDEO_V4L2_SUBDEV_API
    depends on MEDIA_CAMERA_SUPPORT
    default y
    select V4L2_FWNODE
    help
      This is a Video4Linux2 sensor driver for the TechNexion
      TEVS camera sensor with a MIPI CSI-2 interface.
  ```
  > [!NOTE]
  > you can refer to [linux-tn-imx/drivers/media/i2c/Kconfig](https://github.com/TechNexion/linux-tn-imx/blob/tn-imx_5.15.71_2.2.0-next/drivers/media/i2c/Kconfig)
  
  **4.  Modify makefile to add device tree.**
  ```
  $ cd <fatch_kernel_folder>/arch/arm64/boot/dts/freescale/
  ~/<fatch_kernel_folder>/arch/arm64/boot/dts/freescale/$ vi Makefile
  ```
  Add this line in Makefile.
  ```
  dtb-$(CONFIG_ARCH_MXC) += imx8mp-evk-tevs.dtb
  ```
  > [!NOTE]
  > you can refer to [linux-tn-imx/arch/arm64/boot/dts/freescale/Makefile](https://github.com/TechNexion/linux-tn-imx/tree/tn-imx_5.15.71_2.2.0-next/arch/arm64/boot/dts/freescale/Makefile)
  <br/>
  
  **5.  Compile the kernel & module driver**<br/>
  Finally you can start comile your new Image files, then copy and replace the Image files in the SD card.<br/>


## Instructions for testing camera

**Specify camera DTB in u-boot**

1. Connect debug console cable to NXP 8MPLUSLPD4-EVK.
2. Power on board, and enter u-boot prompt.
3. Specify camera dtb via 'fdtfile' u-boot environment variable
  ```
$ setenv fdtfile imx8mp-evk-tevs.dtb
  ```
4. Continue boot process.
  ```
$ saveenv
$ boot
  ```
## Start camera video stream via gstreamer
We can check whether camera have been link via v4l2 control command :
  ```
$ v4l2-ctl --list-device
  ```
Get the device number of camera capture device.
  ```
mxc-isi-cap (platform:32e00000.isi:cap_devic):
       /dev/video{X}
  ```
The following is example.<br/>

<image src="https://github.com/TechNexion-Vision/imx8_evk_tevi/assets/57210123/3d3e9cee-bed8-4a54-b471-17f7f8ad267d"  width="480">

Specify the capture device you just get and start gstreamer to get video stream on screen :
  ```
$ gst-launch-1.0 v4l2src device=/dev/video{X} ! video/x-raw,width=<x>,height=<y> ! waylandsink
  ```

## Additional information

[NXP 8MPLUSLPD4-EVK board TEVI Camera Usage Guide](https://developer.technexion.com/docs/nxp-8mpluslpd4-evk-board-tevi-camera-usage-guide)

<br/><br/><br/><br/><br/>
