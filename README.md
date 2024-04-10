# yocto-rasp4-can
Projeto RASPBERRYPI4 copilação de um ambientes yocto,update do kernel e acesso a uma rede can-bus.

-Hardwares necessarios: 

#Raspberrypi4
#Shield can mcp2515 spi

 1 - Voçe precisa de ambiente linux com pelo menos 100gb de espaço
     Instalar na máquina os requisitos que o Yocto necessita
     Para Ubuntu 22.04:

    sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev zstd liblz4-tool
    
 2 - Abra seu terminal
     Crie uma pasta de nome yocto detro dela faça o seguinte git clone:
     
     git clone -b kirkstone git://git.yoctoproject.org/poky.git
  
 3 - Baixar as metas do projeto:
  
     vá para pasta poky
  
     dentro da pasta poky faça os seguintes git clone:

     git clone -b kirkstone git://git.openembedded.org/meta-openembedded

     git clone -b kirkstone git://git.yoctoproject.org/meta-raspberrypi

  
 4 - Volte para pasta yocto crie um arquivo com o nome de export,"exemplo nano export"
      e edite cole as seguintes instruções:


      #!/bin/sh
      BUILDDIR="../build"
      cd poky
      . ./oe-init-build-env ${BUILDDIR}


      salve e saia do nano.

      execute:
      . export
  
      será criado uma pasta build e voçê sera direcionado para ela.
  
      Dentro da pasta build tera outras subpastas entre dentro da pasta conf e substitua o arquivo local.conf e bblayers.conf 
      pelos que foi fornecido aqui no git
  
      Edite o arquivo bblayers.conf no caminho das metas substitua usuario pelo usuário da sua màquina e salve.
  
  5 - Ainda dentro da pasta build "se nao execute . export dentro da pasta yocto"
       
      execute: 
      
      bitbake-layers show-layers
      
      verifique se nao retorna nenhum erro.
      
      entao vamos compliar:
      
      bitbake core-image-full-cmdline
      
      Esse proceso leva um tempo longo depende muito da sua máquina.
  
  6 - Assim que terminar a compilção será criado uma imagem de nome  core-image-full-cmdline-raspberrypi4.wic.bz2 que 
  
      esta dentro da pasta /home/usuario/yocto/build/tmp/deploy/images com o aplicativo balena contrua a imagem dentrop de um 
      
      sdcard class10 e insira na raspberrypi4 e ligue.
      
  7 - Agora vamos atualizar o kernel:
  
      conecte sua raspberrypi4 na rede conecte um teclado então ligue
      
      vai pedir login digite root
      
      então verifique o ip digite
      
      ifconfig
      
      aproveite e crie uma pasta local:
      
      mkdir rpi-kernel
      
  8 - Volte para  sua maquina baixe a pasta do repositorio chamada rpi-kernel acesse ela com o terminal e digite
  
      o comando substitui "ip da raspberry" pelo ip verificado na raspberrypi4 e execute:
      
      sudo scp -r ./* root@ip da raspberry:/home/root/rpi-kernel 
      
  9 - Vá ate a sua raspberypi4 remotamente ou direto e acesse a pasta rpi-kernel e verifique se contem 2 pastas
  
      boot e lib  apos verificar  se tudo ok digite o seguinte comando:
      
      cp -R ./* /
      
      e depois:
      
      reboot
      
  10 - Execute as ligações da raspberrypi4 com o shield mcp2515 e procedimentos conforme as fotos e o schematic fornecido aqui pelo
      
      repositório.
          
  11 - Vá ate a sua raspberypi4 remotamente ou direto conect a um barramento can obedecendo a conexão High e low, 
      
      certifique qual velocidade do barramento e digite o seguinte comando:
      
      ip link set can0 up type can bitrate 250000
      
      candump can0. Então se tudo estiver ok devera exibir os dados can no terminal.
      
      
      
      
    
      
    
      
      






  
  
  

  

  
  
