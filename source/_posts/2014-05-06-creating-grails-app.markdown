---
layout: post
title: "Creating Grails App"
date: 2014-05-06 11:52:43 +0800
comments: true
categories: 
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


MVC Model View Controll

Grails uses MVC architecture pattern to implement user interface


Syntax in creating Domain (Model)

<code>grails create-domain-class className</code> ex. <code>grails create-domain-class book</code>


Syntax in creating Controller

<code>grails create-controller controllerName</code> ex. <code>grails create-controller bookController</code>


For creating the View

we could simply create a file with .gsp extension name inside the "projectName"/Grails-app/views directory
ex. <code>books.gsp</code>




Basic Grails/Groovy Syntax

just like html tags grails uses opening and closing tags

example of grails form
<pre>
&#60;g:form controller="Persons" action="save" class="grails-form">
            &#60;label>First Name: </label>
            &#60;g:textField name="firstName"/><br/>

            &#60;label>Last Name: </label>
            &#60;g:textField name="lastName"/><br/>

            &#60;label>Age: </label>
            &#60;g:textField name="age"/><br/>

            &#60;g:actionSubmit value="Save"/>
&#60;/g:form>
</pre>

example of grails input field
<code><g:textField name="lastName"/></code>

example of grails submit button
<code><g:actionSubmit value="Save"/></code>

example of looping data to display database content
<pre>
	&#60;table border="1">
		&#60;g:each in="${viewRecords}" status="i" var="thisRecord">
			&#60;tr>
				&#60;td>${thisRecord.id}</td>
				&#60;td>${thisRecord.firstName}</td>
				&#60;td>${thisRecord.lastName}</td>
				&#60;td>${thisRecord.age}</td>
			&#60;/tr>
		&#60;/g:each>
	&#60;/table>
</pre>

Basic Controller Functions

Inserting Data to MySQL Database

<pre>
    def save() {
        def users = new Persons(params)
        users.save()
        render "Success!"
        redirect(action:"view")
    }
</pre>

Pulling data from MySql database
<pre>
    def view = {
    	def viewUsers = Persons.list();
    	[viewRecords: viewUsers];
    }
</pre>

Deleteing data from MySql database with if else statement
<pre>
    def delete = {
    	def deleteUser = Persons.get(params.idNum)

    	if(!deleteUser){
    		render "User Id don't exist!"
    	}else{
	    	deleteUser.delete()
	    	render "Deleted!"
    	}
    	
    }
</pre>

