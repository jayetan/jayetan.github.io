---
layout: post
title: "Installing GVM"
date: 2014-05-06 10:06:53 +0800
comments: true
categories: 
---


Installing GVM (Grails Version Manager)

To install GVM we need to install Curl first via terminal <code>sudo apt-get install curl</code>
then we could follow the instructions in the <code>http://gvmtool.net/</code>

<code>curl -s get.gvmtool.net | bash</code>

after the GVM is installed type this in the terminal <code>gvm help</code>
we should see the list of candidates:
<code>candidate  :  gaiden, gradle, grails, griffon, groovy, groovyserv, lazybones, springboot, vertx</code>
if you are not able to see the candidates list you need to uninstall the GVM and install it again


how to uninstall GVM

we need to delete this <code>#THIS MUST BE AT THE END OF THE FILE FOR GVM TO WORK!!!
[[ -s "~/.gvm/bin/gvm-init.sh" && ! $(which gvm-init.sh) ]] && source "~/.gvm/bin/gvm-init.sh"</code> lines in the 

<code>~/.bash_profile (or ~/.profile)</code>
<code>~/.bashrc</code>
and 
<code>~/.zshrc</code>

just use your text editor to open the file and delete it ex. <code>sudo gedit ~/.bash_profile</code>
then delete the <code>~/.gvm</code> directory <code>rm -rf ~/.gvm</code>

if your GVM installed properly you can now install Grails by typing
<code>gvm install grails [version]</code> ex. <code>gvm install grails 2.1.1</code>
to see the list of available grails type <code>gvm list grails</code>
if you see a note saying that your gvm is in offline mode just put it online by typing <code>gvm offline disable</code>

<small>NOTE: you might think that the code I posted above is not working due to constant errors that you will receive, this is normal, I repeat the steps above numerous times before it installed perfectly, especially in installing the grails, you have to put you gvm in online mode repeatedly because it automatically turns offline when installation fails.</small>