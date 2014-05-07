---
layout: post
title: "Creating Grails App"
date: 2014-05-06 11:52:43 +0800
comments: true
categories: 
published: false
---

Creating Grails App

Before we can create an Grails application, we need to install Java Development kit in our computer by typing
<code>sudo apt-get install oracle-java6-installer</code>
(this will also fixed the JAVA_HOME was NOT set error in your terminal, if you have installed the GVM first.)

after installation we can now create our grails application by typing
<code>grails create-app name</code> ex. <code>grails create-app sampleProject</code>

then <code>cd sampleProject</code> then to run the grails project simply type <code>grails run-app</code>
then browse to <code>http://localhost:8080/sampleProject/</code>
you will now able to see your first grails app.


Configuring Database to use mySQL as default Database

By default Grails uses H2 as its database but we can change this by simply going to your Grails Project then open <code>grails-app/conf/</code> directory then open <code>DataSource.groovy</code>

change

<pre>
dataSource {
    pooled = true
    driverClassName = "org.h2.Driver"
    username = "sa"
    password = ""
}
</pre>

to

<pre>
dataSource {
    pooled = true
    driverClassName = "com.mysql.jdbc.Driver"
    username = "root"
    password = ""
}
</pre>

and change all

<pre>
dbCreate = "update"
url = "jdbc:h2:mem:testDb;MVCC=TRUE;LOCK_TIMEOUT=10000"
</pre>

to

<pre>
dbCreate = "update"
url = "jdbc:mysql://localhost/testing"
</pre>

Then open <code>BuildConfig.groovy</code> find and uncomment the line <code>runtime 'mysql:mysql-connector-java:5.1.16'</code>

<small>
NOTE: dbCreate dictates what grails will do to the database, these are the following definition you can use:

create-drop - Drop and re-create the database when Grails is run
create - Create the database if it doesn't exist, but don't modify it if it does. Deletes existing data.
update - Create the database if it doesn't exist, and modify it if it does exist

<code>-Both create-drop and create will destroy all existing data-</code>
</small>



Basic Grails/Groovy Syntax

just like html tags grails uses opening and closing tags
