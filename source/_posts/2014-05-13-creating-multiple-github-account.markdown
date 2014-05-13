---
layout: post
title: "Creating Multiple Github Account"
date: 2014-05-13 14:36:52 +0800
comments: true
categories: 
---

Creating Multiple Github Account on a Single Machine<br />
(don't change your default github if you have octopress site in your personal github)

In case you already have a personal Github account and want to create a new one for your projects or your client on a single machine (computer) follow this easy steps.


Create a new ssh key by typing in the terminal
<code>ssh-keygen -t rsa -C "email address"</code>
a prompt will show asking where to save the generated key, be carefull not to overwrite your existing key, just save it as ex. <code>~/.ssh/id_rsa_clientName</code>

Then go to ~/.ssh using terminal, type <code>gedit id_rsa_clientName.pub</code> then copy the whole line then login your new github account, go to settings-account settings-ssh key click Add SSH key, give your ssh key a title and then paste your ssh key.

next thing you want to do is to identify the new ssh key by typing <code>ssh-add ~/.ssh/id_rsa_clientName</code> this will allow you to sign in to your github account using the new ssh key, it also tells the git which key should it use to access your github account, this will also fixed the error: Agent admitted failure to sign using the ssh key.

assuming your still on the .ssh folder, create a config file by typing <code>touch config</code> then type in <code>gedit config</code> then paste this line of text
<pre>
#Default GitHub
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa

Host github-clientName
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_clientName
</pre>
this is where we will specify the new github hostname notice the "Host github.com" that is our default github while the "Host github-clientName" is our new github account.

after this we can now push to our new github account, but we need first to create a new repository and copy the git repository url ex. <code>git@github.com:clientName/projectName.git</code> we will be copying only the "clientName/projectName.git" because we will specify the git remote origin by typing <code>git remote add origin github-clientName:clientName/projectName.git</code>
(this is also applicable if you are pulling/cloning an existing repository)


Note: As I stated above if you wish to have an multiple github account but already have an personal github account with octopress in it, you should not make that as your secondary github account, you will able to push to source but you cannot use "rake deploy" to push a new blog.


<small>tags: octopress rake deploy error on multiple github accounts, github multiple accounts, Agent admitted failure to sign using the ssh key</small>