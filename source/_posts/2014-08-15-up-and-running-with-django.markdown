---
layout: post
title: "Up and Running with Django"
date: 2014-08-15 22:55:06 +0800
comments: true
categories: 

---


What is Django?

<a href="http://en.wikipedia.org/wiki/Django_(web_framework)">Django</a> is a free and open source web application framework, written in Python, which follows the model–view–controller architectural pattern.
Django's primary goal is to ease the creation of complex, database-driven websites. Django emphasizes reusability and "pluggability" of components, rapid development, and the principle of don't repeat yourself. Python is used throughout, even for settings, files, and data models. Django also provides an optional administrative create, read, update and delete interface that is generated dynamically through introspection and configured via admin models.



How to install

first download the tarball of django at https://www.djangoproject.com/download/
extract it and via terminal go to the extracted folder of django, then type
<pre>
sudo python setup.py install
</pre> 
if it didn't work you can read the README.rst which can be found at the extracted django folder and read the instruction on how to install it.



Listing all available commands

to list all available Django commands just type
<pre>
django-admin.py
</pre>



Creating django project

just type
<pre>
django-admin.py startproject django_test
</pre>

where in django_test is the name of your project, after installing, a folder with name django_test will be created it will also contains django files.



Running django server
<pre>
python manage.py runserver
</pre>

this will run the django server on localhost:8000, just view it on you browser and you will able to see this line "It worked! Congratulations on your first Django-powered page."



Changing the Django default page using templates

in settings.py add these lines
<pre>
TEMPLATE_DIRS = (
	os.path.join(BASE_DIR, 'templates'),
)
</pre>

then on urls.py add this line in the top page
<pre>
from django.views.generic import TemplateView
</pre>

then include this on urlpatterns inside urls.py
<pre>
url(r'^$', TemplateView.as_view(template_name="index.html")),
</pre>

then make a folder name templates inside your project, inside that templates folder create an index.html and add you html codes.



Creating an App
<pre>
python manage.py startapp article
</pre>

where article is the name of the app



Make views.py in apps use template

put this on top of the page to be able to pass variables and use template
<pre>
from django.template.loader import get_template
from django.template import Context
</pre>

then on views define a function
<pre>
def article(request):
	name = "Jaye"
	template = get_template('article.html')
	html = template.render(Context({'name': name}))
	return HttpResponse(html)
</pre>



The simpliest way rendering template
<pre>
from django.shortcuts import render_to_response
</pre>

then define a function
<pre>
def article(request):
	name = "Jaye"
	return render_to_response("article.html", {"name": name})
</pre>



Rendering template via class definition (can also be used in changing django default page)

assuming you have already imported TemplateView
<pre>
class articleTemplate(TemplateView):
	template_name = "article.html"
	def get_context_data(self, **kwargs):
		context = super(articleTemplate, self).get_context_data(**kwargs)
		context["name"] = "Jaye"
		context["test"] = "Admin"
		return context
</pre>



Creating template that includes external header and footer or anything you want.

this is usefull if you have multiple pages that has the same header and footer.

first we create our html files, index.html, &#95;header.html, and &#95;footer.html
now open up index.html, then use &#123;&#37; include &#37;&#125; to include the other html files
<pre>
&lt;!DOCTYPE html>
&lt;html>
&lt;head>
	&lt;title>&lt;/title>
&lt;/head>
&#123;&#37; include "_header.html" &#37;&#125;
&lt;body>
	
	BODY CONTENTS HERE

&#123;&#37; include "_footer.html" &#37;&#125;
&lt;/body>
&lt;/html>
</pre>

while the &#95;header and &#95;footer.html can contain any html tags except for &lt;html>&lt;/html> and &lt;body>&lt;/body>


Enabling Django Admin

go to settings.py and uncomment these lines
<pre>
'django.contrib.admin',
'django.contrib.auth',
</pre>

and

go to urls.py and uncomment these lines
<pre>
from django.contrib import admin
admin.autodiscover()
url(r'^admin/', include(admin.site.urls)),
</pre>

after this you will now able to log in the admin page of django http://localhost:8000/admin