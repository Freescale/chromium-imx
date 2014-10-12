Freescale i.MX VPU hardware video decoding support for Chromium's GPU media stack
=================================================================================

This repository contains sources which add hardware video decoding support to Chromium
using the Freescale i.MX VPU. They are placed under the BSD 3-clause license. See the
LICENSE file for details.

These sources are written against Chromium 38.0.2125.101.


Prerequisites
-------------

The i.MX platform requires the Vivante GPU drivers and userspace libraries to be installed.
The patches make use of Vivante specific OpenGL ES 2.0 extension to ensure zero-copy display
of decoded frames.

Also, Freescale's libfslvpuwrap library is required. Use at least version 1.0.45.

Furthermore, Chromium must be ran with its EGL backend enabled. Use the --use-gl=egl option for this.


Patching Chromium
-----------------

1. Copy the contents of src/ to the Chromium source tree.
2. Apply all patches from patches/common/ in the source tree which are not version specific.
3. If you are using a Chromium build that has already been patched with ozone-wayland, also apply
   the patches in patches/wayland/ . Note that it patches ozone-wayland files.
4. Build Chromium. chromium://gpu should show video decoding as "Accelerated".
