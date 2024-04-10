# yocto-rasp4-can
Projeto RASPBERRYPI4 copilação de um ambientes yocto,update do kernel e acesso a uma rede can-bus.
-Hardwares necessarios: 
#Raspberrypi4
#Shield can mcp2515 spi

1 - Voçe precisa de ambiente linux com pelo menos 100gb de espaço
Instalar na máquina os requisitos que o Yocto necessita
- Para Ubuntu 22.04:
sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat
cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git
python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev
zstd liblz4-tool
2 - Abra seu terminal
  Crie uma pasta de nome yocto ou o nome que voçê desejar faça dentro desta pasta:
  git clone -b kirkstone git://git.yoctoproject.org/poky.git
  Dentro da pasta crie um arquivo com o nome de export,exemplo touch export
  abra esse arquivo com o nano e edite cole as seguintes instruções:


  #!/bin/sh
  BUILDDIR="../build"
  cd poky
. ./oe-init-build-env ${BUILDDIR}


  salve e saia do nano.

  execute:
   . export
  

  
  
