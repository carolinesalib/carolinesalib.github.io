---
layout: post
title: Problema de certificado SSL ao baixar uma box no vagrant!
categories: [vagrant]
tags: [vagrant, ssl, certificado, error, download, box, certificate]
fullview: true
comments: true
---

Olá, hoje ao tentar iniciar uma nova box utilizando Vagrant, acabei tendo problemas com certificação. Como não achei solução específica e em português pela internet, resolvi compartilhar pra ajudar quem possa ter o mesmo problema.

**Problema retornado pelo GitShell no windows:**

An error occurred while downloading the remote file. The error
message, if any, is reproduced below. Please fix this error and try
again.

{% highlight yaml %}
SSL certificate problem: unable to get local issuer certificate
More details here: http://curl.haxx.se/docs/sslcerts.html

curl performs SSL certificate verification by default, using a "bundle"
 of Certificate Authority (CA) public keys (CA certs). If the default
 bundle file isn't adequate, you can specify an alternate file
 using the --cacert option.
If this HTTPS server uses a certificate signed by a CA represented in
 the bundle, the certificate verification probably failed due to a
 problem with the certificate (it might be expired, or the name might
 not match the domain name in the URL).
If you'd like to turn off curl's verification of the certificate, use
 the -k (or --insecure) option.
{% endhighlight %}


**Solução encontrada:**

O comando abaixo foi adicionado no meu Vagrantfile para que ignorasse o certificado SSL que estava impedindo o download da box.

<code>
config.vm.box_download_insecure = "https://caminhoparadownload.nomedabox.box"
</code>

Após alterado o Vagrantfile, basta executar "vagrant up" novamente.

Referencias:
https://docs.vagrantup.com/v2/vagrantfile/machine_settings.html
