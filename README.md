# LeMa (LED Machine)

LeMa is an example Yocto project to run on Raspberry Pi 4 hardware to control
external LED controller hardware, like switch and MOSFET boards.

## Requirements

* Python
* KAS Python library (>=3.2.3)
* docker
* Raspberry Pi 4
* bmap-tools (for image flashing)
  
## Build

The Raspberry Pi image is created by a bitbake (Yocto) build process. For
convenience reasons the [KAS](https://pypi.org/project/kas/) bitbake configuration
and build management tool is used.

```
python -m pip install kas
```

Before you start the build please configure the appropriate root password within
_'lema.yml'_ file by setting the appropriate value to the `ROOT_PASSWORD` variable!

After KAS was successfully installed, you could simply start the image build process
with the following command. During that process the tools will fetch different
files and repositories to your local space, compiles all needed programs as well as
the kernel and pack the system image, which could take a while!

```
kas-container build lema.yml
```

If the images has been built successfully you can directly flash the image
to the SD-Card by calling the `bmaptool`.

```
sudo bmaptool copy --bmap build/tmp/deploy/images/raspberrypi4/core-image-base-lema-raspberrypi4.wic.bmap build/tmp/deploy/images/raspberrypi4/core-image-base-lema-raspberrypi4.wic.bz2 /dev/sdb
```

## License

[LGPLv2.1](https://www.gnu.de/documents/lgpl-2.1.de.html)