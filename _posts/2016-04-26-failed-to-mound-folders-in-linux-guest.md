---
layout: post
title: Failed to mound folders in linux guest
categories: [vagrant]
tags: [vagrant, virtualbox, linux, ubuntu, guest, folders, failed]
fullview: true
comments: true
---

**Problema**

{% highlight yaml %}
Failed to mount folders in Linux guest. This is usually because the "vboxsf" file system is not available. Please verify that the guest additions are properly installed in the guest and can work properly. The command attempted was:

mount -t vboxsf -o uid=id -u vagrant,gid=getent group vagrant | cut -d: -f3 home_vagrant_ieducar /home/vagrant/ieducar mount -t vboxsf -o uid=id -u vagrant,gid=id -g vagrant home_vagrant_ieducar /home/vagrant/ieducar

The error output from the last command was:

stdin: is not a tty mount: unknown filesystem type 'vboxsf'
{% endhighlight %}

**Solução**

Caso este erro aconteça ao iniciar sua máquina virtual, execute o comando abaixo para que suas pastas sejam compartilhadas corretamente.

<code>
vagrant plugin install vagrant-vbguest

vagrant up; vagrant ssh -c 'sudo ln -s /opt/VBoxGuestAdditions-4.3.10/lib/VBoxGuestAdditions /usr/lib/VBoxGuestAdditions'; vagrant reload
</code>
