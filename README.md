# Mali support for Rockchip platforms

This driver builds as a module against recent mainline kernels
(5.4+). It brings support for Mali Bifrost GPUs found on Rockchip
SoCs.

There is almost nothing specific to Rockchip here as this work is
based on the [official ARM r8p0-01rel0 Linux driver](https://developer.arm.com/tools-and-software/graphics-and-gaming/mali-drivers/bifrost-kernel).

## Device tree configuration

Device tree bindings are already upstream for [Mali Bifrost drivers](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/devicetree/bindings/gpu/arm,mali-bifrost.yaml).

## Build and installation

You need a cross-compilation toolchain configured properly.

```
git clone https://github.com/miquelraynal/rockchip-mali.git
cd rockhip-mali
make -j4 KDIR=<linux-sources>
cp $(find -name mali_kbase.ko) <target-directory>
```

## User-space components

Checkout the libraries from Rockchip's Mali blobs repository:

```
https://github.com/rockchip-linux/libmali
```

Inspired by Maxime Ripard's work,
https://github.com/mripard/sunxi-mali
