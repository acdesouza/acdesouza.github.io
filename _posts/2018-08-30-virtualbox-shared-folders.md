---
layout: post
title: VirtualBox - Configurar shared folder entre host e guest
tags:
- beginner
- virtualbox
---
Um breve tutorial para compartilhar uma pasta
do host com o guest, no caso, um Debian 8.8.
No meu caso, para editar código-fonte no host e
ver as modificações no guest, mais próximo ao sistema
que irá rodar o código em produção.

# Configurando a shared folder no VirtualBox

Essa é a parte tranquila ;)

## No host

Seleciona a imagem máquina que terá a pasta compartilhada.

  * Configuracões > Pastas compartilhadas > Acresenta uma nova pasta compartilhada
  * Caminho para a pasta: seleciona a pasta no host
  * Nome da pasta: é a que será usada para montar a pasta no Guest

## No guest

É aqui que tive problemas. Estou usando o Debian 8.8. Instalando pela versão firmware-8.8.0-amd64-netinst.iso.
E, aí que, além de tudo ele não monta o cd automagicamente. :/

  * Com a máquina virtual iniciada, selecione a opção de menu: ```Devices > Insert Guest Additions CD image...```
  * Abre o terminal:

{% highlight bash %}
$ sudo apt-get install build-essential module-assistant
$ sudo m-a prepare
$ sudo mount /media/cdrom
$ sudo sh /media/cdrom/VBoxLinuxAdditions.run
{% endhighlight %}

Para ver se está tudo certo, pede pro Virtualbox listar as shared folders:

{% highlight bash %}
$ sudo VBoxControl sharedfolder list

Oracle VM VirtualBox Guest Additions Command Line Management Interface Version 5.2.18
(C) 2008-2018 Oracle Corporation
All rights reserved.

Shared Folder mappings (1):

01 - sisteminha
{% endhighlight %}

Para montar a pasta do host ```/Projects/sisteminha``` no guest em ```~/sisteminha```

{% highlight bash %}
sudo mount -t vboxsf sisteminha ~/sisteminha/
{% endhighlight %}

Para montar automagicamente no boot, adiciona no ```/etc/fstab```

{% highlight bash %}
sisteminha   /home/usuario/sisteminha   vboxsf   defaults  0   0
{% endhighlight %}


E, aí que, pode dar o erro ```VirtualBox: mount.vboxsf: mounting failed with the error: No such device```.

Para resolver:

{% highlight bash %}
$ cd /opt/VBoxGuestAdditions-*/init
$ sudo ./vboxadd setup
{% endhighlight %}

E, foi assim que consegui usar o host para editar o código e testar no guest.

Na próxima vez eu acho que deveria reconsiderar o uso do Vagrant...


# Fontes

  * [VirtualBox Manual](https://www.virtualbox.org/manual/ch04.html#sharedfolders)
  * [Installing Guest Additions on Debian](https://virtualboxes.org/doc/installing-guest-additions-on-debian/)
  * [Fixing VirtualBox: mount.vboxsf: mounting failed with the error: No such device](https://stackoverflow.com/a/29456128/436552)
