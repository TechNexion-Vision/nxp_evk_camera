# NXP EVK Camera Driver

[![Technexion](https://github.com/user-attachments/assets/c78973b8-4967-4d72-8082-5d6b9ef5dc99)](https://www.technexion.com/products/embedded-vision/)


[![Producer: Technexion](https://img.shields.io/badge/Producer-Technexion-blue.svg)](https://www.technexion.com)
[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

## Introduction

[TechNexion Embedded Vision Solutions](https://www.technexion.com/products/embedded-vision/) provide embedded system developers access to high-performance, industrial-grade camera solutions to accelerate their time to market for embedded vision projects.

## Supported NXP i.MX EVK

- [i.MX 8M Plus EVK - 8MPLUSLPD4-EVK](https://www.nxp.com/design/design-center/development-boards-and-designs/8MPLUSLPD4-EVK)
- [i.MX 93 EVK - iMX93LPDDR4X-EVK](https://www.nxp.com/design/design-center/development-boards-and-designs/i.MX93EVK)
- [i.MX 95 EVK - iMX95LPD5EVK-19CM](https://www.nxp.com/products/iMX95?tid=vaniMX95)

## Supported System Version

- [TechNexion Yocto 5.0 Scarthgap 6.6.y GA BSP](https://github.com/TechNexion/tn-imx-yocto-manifest/tree/scarthgap_6.6.y-stable)

## Supported Camera Modules

| **Camera Series** | **Products** |
| --- | --- |
| TEVS | TEVS-AR0144-C<br>TEVS-AR0145-M<br>TEVS-AR0234-C<br>TEVS-AR0521-C<br>TEVS-AR0522-C<br>TEVS-AR0522-M<br>TEVS-AR0821-C<br>TEVS-AR0822-C<br>TEVS-AR1335-C |

[More Camera Products Details...](https://www.technexion.com/products/embedded-vision)

## Install TN Camera on NXP EVK

### Adaptor for NXP EVK

-  MINI-SAS Adaptor for **i.MX 8M Plus EVK**

    > Connect TEVS camera and MINI-SAS adaptor to **i.MX 8M Plus EVK**.

    <a href="https://www.technexion.com/shop/embedded-vision/mipi-csi2/evk/tevs-ar0144-c-s83-ir-nxp/" target="_blank">
    <img src="https://www.technexion.com/wp-content/uploads/2024/11/tevs-ar0144-c-s83-ir-nxp.png" width="240" />
    </a>

- TEV-RPI22 Adaotor for **i.MX 93 EVK**

    > Connect TEVS camera and TEV-RPI22 adaptor to **i.MX 93 EVK**.

    <a href="https://www.technexion.com/products/embedded-vision/mipi-csi2/evk/tevs-ar0144-c-s83-ir-rpi22/" target="_blank">
    <img src="https://www.technexion.com/wp-content/uploads/2024/11/tevs-ar0144-c-s83-ir-rpi22.png" width="240" />
    </a>

- MINI-SAS Adaptor for **i.MX 95 EVK**

    > Connect TEVS camera and MINI-SAS adaptor to **i.MX 95 EVK**.

    <a href="https://www.technexion.com/shop/embedded-vision/mipi-csi2/evk/tevs-ar0144-c-s83-ir-nxp/" target="_blank">
    <img src="https://www.technexion.com/wp-content/uploads/2024/11/tevs-ar0144-c-s83-ir-nxp.png" width="240" />
    </a>

### Method 1 - Using TechNexion Pre-built image

The demo image contains the required device tree blobs and camera drivers to enable TechNexion TEVS Series cameras.
Choose the correct demo image that is compatible with the EVK board you have.

Prebuilt demo images can be available for download via TechNexion's server.

- [i.MX 8M Plus EVK](https://download.technexion.com/demo_software/EVK/NXP/IMX8MP-LPDDR4/imx8mp-lpddr4-evk_yocto-5.0-qt6_20241230.zip)
- [i.MX 93 EVK](https://download.technexion.com/demo_software/EVK/NXP/IMX93-LPDDR4X/imx93-11x11-lpddr4x-evk_yocto-5.0-qt6_20241230.zip)
- [i.MX 95 EVK](https://download.technexion.com/demo_software/EVK/NXP/IMX95-LPDDR5/imx95-19x19-lpddr5-evk_yocto-5.0-qt6_20241230.zip)


> [!TIP]
> Ensure the boot mode is configured as **boot from SD card**. <br/>
> Following this page to boot up *i.MX 8M Plus EVK*: [Getting Started with the i.MX 8M Plus EVK](https://www.nxp.com/document/guide/getting-started-with-the-i-mx-8m-plus-evk:GS-iMX-8M-Plus-EVK) <br/>
> Following this page to boot up *i.MX 93 EVK*: [Getting Started with the i.MX93 EVKK](https://www.nxp.com/document/guide/getting-started-with-the-i-mx93-evk:GS-IMX93EVK) <br/>
> Following this page to boot up *i.MX 95 EVK*: [i.MX 95 LPD5 EVK Quick Start Guide](https://www.nxp.com/docs/en/quick-reference-guide/IMX95LPD5EVK-19CM.pdf)
>
> SD card capacity must be > 8GB and then Flash image to SD card.
>   - Under Windows flash tool： [balena etcher](https://www.balena.io/etcher/)
>   - Under Linux flash tool： [bmap-tools](https://github.com/intel/bmap-tools)


### Method 2 - Build Yocto image with TechNexion BSP

If you want to build a Yocto Project image by yourself, TechNexion BSP release providing support NXP i.mx series processors：

[Fetch Yocto source](https://github.com/TechNexion/tn-imx-yocto-manifest/tree/scarthgap_6.6.y-stable)<br/>
[Build Yocto](https://github.com/TechNexion/tn-imx-yocto-manifest/tree/scarthgap_6.6.y-stable?tab=readme-ov-file#for-nxp-evk-with-technexion-tevs-and-vls-camera-support)

### Method 3 - Build Linux kernel with TechNexion source code

1. Download the camera driver and device tree blobs.

    ```shell
    $ git clone https://github.com/TechNexion-Vision/nxp_evk_camera.git -b tn-imx_6.6.52_2.2.0-stable
    ```

2. Copy to your kernel source code.

    ```shell
    $ cd nxp_evk_camera/
    ~/nxp_evk_camera$ cp -r driver/media/i2c/tevs/ <fetch_kernel_folder>/driver/media/i2c/

    # for i.MX 8M Plus EVK
    ~/nxp_evk_camera$ cp arch/arm64/boot/dts/freescale/imx8mp-evk-tevs.dts <fetch_kernel_folder>/arch/arm64/boot/dts/freescale/

    # for i.MX 93 EVK
    ~/nxp_evk_camera$ cp arch/arm64/boot/dts/freescale/imx93-11x11-evk-tevs-rpi22.dts <fetch_kernel_folder>/arch/arm64/boot/dts/freescale/

    # for i.MX 95 EVK
    ~/nxp_evk_camera$ cp arch/arm64/boot/dts/freescale/imx95-19x19-evk-tevs-tev-nxp.dts <fetch_kernel_folder>/arch/arm64/boot/dts/freescale/
    ```

3. Modify makefile to add driver.

    ```shell
    $ cd <fetch_kernel_folder>/driver/media/i2c/
    ~/<fetch_kernel_folder>/driver/media/i2c/$ vi Makefile
    ```

    Add this line in Makefile.
    ```shell
    obj-$(CONFIG_VIDEO_TEVS) += tevs/
    ```

> [!NOTE]
> you can refer to [linux-tn-imx/drivers/media/i2c/Makefile](https://github.com/TechNexion/linux-tn-imx/blob/tn-imx_6.6.52_2.2.0-stable/drivers/media/i2c/Makefile)

4. Modify Kconfig to add camera config.

    ```shell
    ~/<fetch_kernel_folder>/driver/media/i2c/$ vi Kconfig
    ```

    Add this part under "Camera sensor devices" menu in Kconfig.
    ```shell
    config VIDEO_TEVS
      tristate "TechNexion TEVS sensor support"
      depends on OF
      depends on GPIOLIB && I2C && VIDEO_V4L2_SUBDEV_API
      depends on MEDIA_CAMERA_SUPPORT
      select V4L2_FWNODE
      default y
      help
        This is a Video4Linux2 sensor driver for the TechNexion
        TEVS camera sensor with a MIPI CSI-2 interface.
    ```

> [!NOTE]
> you can refer to [linux-tn-imx/drivers/media/i2c/Kconfig](https://github.com/TechNexion/linux-tn-imx/blob/tn-imx_6.6.52_2.2.0-stable/drivers/media/i2c/Kconfig)

5. Modify makefile to add device tree.

    ```shell
    $ cd <fetch_kernel_folder>/arch/arm64/boot/dts/freescale/
    ~/<fatch_kernel_folder>/arch/arm64/boot/dts/freescale/$ vi Makefile
    ```

    Add this line in Makefile.
    ```shell
    # for i.MX 8M Plus EVK
    dtb-$(CONFIG_ARCH_MXC) += imx8mp-evk-tevs.dtb

    # for i.MX 93 EVK
    dtb-$(CONFIG_ARCH_MXC) += imx93-11x11-evk-tevs-rpi22.dtb

    # for i.MX 95 EVK
    imx95-19x19-evk-tevs-dtbs := imx95-19x19-evk.dtb imx95-19x19-evk-tevs-tev-nxp.dtbo
    dtb-$(CONFIG_ARCH_MXC) += imx95-19x19-evk-tevs.dtb
    ```

> [!NOTE]
> you can refer to [linux-tn-imx/arch/arm64/boot/dts/freescale/Makefile](https://github.com/TechNexion/linux-tn-imx/blob/tn-imx_6.6.52_2.2.0-stable/arch/arm64/boot/dts/freescale/Makefile)

6. Compile the kernel & module driver.

    Finally, you can start compiling your new Image files, then copy and replace the Image files in the SD card.

## Instructions for testing camera

### Specify camera DTB in u-boot

1. Connect debug console cable to NXP EVK.

2. Power on board, and enter u-boot prompt.

3. Specify camera dtb via `fdtfile` u-boot environment variable

    ```shell
    # for i.MX 8M Plus EVK
    u-boot=> setenv fdtfile imx8mp-evk-tevs.dtb

    # for i.MX 93 EVK
    u-boot=> setenv fdtfile imx93-11x11-evk-tevs-rpi22.dtb

    # for i.MX 95 EVK
    u-boot=> setenv fdtfile imx95-19x19-evk-tevs-tev-nxp.dtb
    ```

4. Continue boot process.

    ```shell
    u-boot=> saveenv
    u-boot=> boot
    ```

### Start camera video stream via gstreamer

We can check whether camera have been link via v4l2 control command :

  ```shell
  $ v4l2-ctl --list-device
  ```

Get the device number of camera capture device.

  ```shell
  mxc-isi-cap (platform:32e00000.isi:cap_devic):
        /dev/video{X}
  ```

The following is an example.<br/>

<image src="https://github.com/TechNexion-Vision/imx8_evk_tevi/assets/57210123/3d3e9cee-bed8-4a54-b471-17f7f8ad267d"  width="480">

Specify the capture device you just get and start Gstreamer to get video stream on screen :

  ```shell
  $ gst-launch-1.0 v4l2src device=/dev/video{X} ! video/x-raw,width=<x>,height=<y> ! waylandsink
  ```

## Additional information

[NXP 8MPLUSLPD4-EVK board TEVS Camera Usage Guide](https://developer.technexion.com/docs/nxp-8mpluslpd4-evk-board-tevs-camera-usage-guide) <br/>
[NXP IMX93LPDDR4X-EVK board TEVS Camera Usage Guide](https://developer.technexion.com/docs/nxp-imx93lpddr4x-evk-board-tevs-camera-usage-guide) <br/>
[NXP IMX95LPD5EVK-19CM board TEVS Camera Usage Guide](https://developer.technexion.com/docs/nxp-imx95lpd5evk-19cm-board-tevs-camera-usage-guide)
<br/><br/>
