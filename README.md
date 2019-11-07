# meta-licheepizero

# Yocto meta layer for Lichee Pi Zero and Lichee Pi Zero Dock

## How to build an images

General Note:
Assumed that Linux Ubuntu is installed

1. First make sure to following packages are installed in system

	sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib \
	build-essential chrpath socat libsdl1.2-dev xterm

Note:
More informations can be found on Yocto reference manual.

2. Download necessary Yocto packaged listed below

	git clone git://git.yoctoproject.org/poky --depth 1 -b zeus <br>
cd poky <br>
	git clone git://git.openembedded.org/meta-openembedded --depth 1 -b zeus <br>
	git clone https://github.com/meta-qt5/meta-qt5.git --depth 1 -b zeus <br>
	git clone <br>

3. Select directory to build Linux

	source oe-init-build-env ~/yocto/build/licheepizero <br>
or <br>
	source oe-init-build-env ~/yocto/build/licheepizero-dock <br>

4. Modify bblayers.conf PATH

BBLAYERS ?= " \
  ${HOME}/yocto/poky/meta \
  ${HOME}/yocto/poky/meta-poky \
  ${HOME}/yocto/poky/meta-openembedded/meta-oe \
  ${HOME}/yocto/poky/meta-openembedded/meta-networking \
  ${HOME}/yocto/poky/meta-openembedded/meta-python \
  ${HOME}/yocto/poky/meta-qt5 \
  ${HOME}/yocto/poky/meta-licheepizero \
  "

5. Modify local.conf file

    - align DL_DIR ?= "${HOME}/yocto/downloads" <br>

    - align SSSTATE_DIR ?= "${HOME}/yocto/sstate-cache" <br>
    
    - align TMPDIR ?= "${HOME}/yocto/tmp" <br>

    Note: Please adapt rest of conf/local.conf parameters if necessary. <br>

6. Build objects

    - console image
      bitbake console-image <br>

    - qt5 image
      bitbake qt5-image <br>

    - qt5 toolchain sdk
      bitbake meta-toolchain-qt5 <br>

7. After compilation images appears in

	~/yocto/tmp/deploy/images/licheepizero <br>
or <br>
	~/yocto/tmp/deploy/images/licheepizero-dock <br>
