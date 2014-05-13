---
layout: post
title: "Installing Drupal locally"
date: 2014-05-07 11:39:26 +0800
comments: true
categories:
---

Installing Drupal on Localhost

In order to run Drupal locally we must have a Server that runs Apache, Php and MySQL,
for windows you can install software bundle called wamp
for mac you can use mamp
and for linux you can install lamp, but I recommend to install it individually, in my experience as a linux user installing a bundle package will cause you a lot of errors rather than installing it individually.

Installing Apache, PHP MySQL and PHPmyadmin for LINUX

Open terminal and type in these commands:

APACHE

<code>sudo apt-get</code>
<code>sudo apt-get install apache2</code>
to test if the apache is working browse <code>http://localhost</code>


MySQL
<code>sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql</code>
<code>sudo mysql_install_db</code>
<code>sudo /usr/bin/mysql_secure_installation</code>
prompt will appear asking for current password for root
<pre>Enter current password for root (enter for none): 
OK, successfully used password, moving on...</pre>
for testing purposes I would recommend to not put password for root,
a bunch of promt questions will follow along installation just type y to all.

PHP

<code>sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt</code>

PHPmyadmin

<code>sudo apt-get install phpmyadmin</code>

after you installed the LAMP

download the drupal at <code>https://drupal.org/download</code>
choose the .zip format and unzipped it after download to see the drupal folder
use the terminal to move the drupal folder to var/www by typing <code>sudo mv Downloads/Drupal-7.27 /var/www</code>

Note: You may need to grant access to your /var/www folder to do this simply type the following:
<pre>
sudo chmod -R 777 /var/www
sudo chown -R **yourusername** /var/www
</pre>

Next thing you must do is to setup the database for your drupal, browse http://localhost/phpmyadmin
and create a database for your drupal.

then browse http://localhost/drupal folder name ex. http://localhost/drupal-7.27 this will take you to the installation, just follow the instruction and you wil be able to install drupal.