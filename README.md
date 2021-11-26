NXP IMX8 EVK with TEVI camera support
===========================

![](https://img.shields.io/badge/Release-REV01-green.svg)
![](https://img.shields.io/badge/Producer-Technexion-blue.svg)
![](https://img.shields.io/badge/License-GPL3.0-orange.svg)


## Support Hardware
 --------
|NXP EVK| Support sensor |
|---|---|
|IMX8MP-EVK| TEVI-OV5640 <br> TEVI-AR0521 <br> TEVI-AR0144 <br> TEVI-AR0234 |
|IMX8MM-EVK| will be released soon |

## BSP Requirement
 --------
[Yocto 3.3 with Kernel 5.10.52](https://www.nxp.com/design/software/embedded-software/i-mx-software/embedded-linux-for-i-mx-applications-processors:IMXLINUX?tab=In-Depth_Tab)

## User Guide
   --------

#### Merge relate patches to Kernel source

Step 1. Prepare Linux Kernel source code, note that the version must be kernel 5.10.52 or above

    $ git clone https://source.codeaurora.org/external/imx/linux-imx.git
    $ cd linux-imx
    $ git checkout lf-5.10.52-2.1.0

Step 2-1. Merge patches using github way (recommended)

    $ cp -rv imx-evk_tevi-bsp/imx8mp-evk/git_patches/*.patch linux-imx
    $ cd linux-imx
    $ git am -3 *.patch
    $ rm *.patch

Step 2-2. You also can merge patches using copy/paste way (It's alterlative way)

    $ cp -rv imx8mp-evk/src/arch/arm64/boot/dts/freescale/* linux-imx/arch/arm64/boot/dts/freescale/
    $ cp -rv imx8mp-evk/src/arch/arm64/configs/imx_v8_defconfig linux-imx/arch/arm64/configs/imx_v8_defconfig
    $ cp -rv imx8mp-evk/src/drivers/media/i2c/* linux-imx/drivers/media/i2c/

Step 3. Recompile kernel image and dtb files

Step 4. Update kernel image and dtb files in runtime image

Step 5. Change loaded dtb file in the runtime of u-boot prompt (do one time only)

    Hit any key to stop autoboot:  0

    (Enable TEVI-OV5640 on CSI1 port if you want)
    u-boot=> setenv fdtfile imx8mp-evk-tevi-ov5640-csi1.dtb

    (Enable TEVI-OV5640 on CSI2 port if you want)
    u-boot=> setenv fdtfile imx8mp-evk-tevi-ov5640-csi2.dtb

    (Enable TEVI-AR0521 on CSI1 port if you want)
    u-boot=> setenv fdtfile imx8mp-evk-tevi-ar0521-csi1.dtb

    (Enable TEVI-AR0521 on CSI2 port if you want)
    u-boot=> setenv fdtfile imx8mp-evk-tevi-ar0521-csi1.dtb

    (Enable TEVI-AR0144 on CSI1 port if you want)
    u-boot=> setenv fdtfile imx8mp-evk-tevi-ar0144-csi1.dtb

    (Enable TEVI-AR0144 on CSI2 port if you want)
    u-boot=> setenv fdtfile imx8mp-evk-tevi-ar0144-csi2.dtb

    (Enable TEVI-AR0234 on CSI1 port if you want)
    u-boot=> setenv fdtfile imx8mp-evk-tevi-ar0234-csi1.dtb

    (Enable TEVI-AR0234 on CSI2 port if you want)
    u-boot=> setenv fdtfile imx8mp-evk-tevi-ar0234-csi2.dtb

    u-boot=> saveenv
    u-boot=> boot

#### How to use TEVI cameras after merged patches


|Sensors|
|---|
|TEVI-OV5640 |
|[TEVI-AR0521](https://developer.technexion.com/docs/usage-guide-on-imx8m-plus-edm-g-wb2021-q4-release) |
|[TEVI-AR0144](https://developer.technexion.com/docs/usage-guide-on-wb-edm-g-imx8m-plus2021-q4-release) |
|[TEVI-AR0234](https://developer.technexion.com/docs/usage-guide-on-wb-edm-g-imx8m-plus2021-q4-release-1) |
