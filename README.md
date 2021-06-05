<h1>Django allauth package</h1>

<i>Core steps to configure the allauth package in your project in order to login with google accounts</i>

<h3>Set a virtual environment</h3>
<p>
<code>$ virtualenv venv</code> where venv is the name of your virtual environment

<code>$ source venv/bin/activate</code>
</p>

<h3>Install Django</h3>
<p>
<code>pip install django</code>

or specifying the version   
<code>pip install django==3.0</code>

install django allauth 
<code>$ pip install django-allauth</code>   
</p>

<h3>Create Django Project</h3>
Into the project folder:
<p>
<code>$ django-admin startproject <i>name</i> .</code>
</p>

<h3>Create Django App</h3>
<p>
<code>django-admin startapp <i>name</i></code>
</p>

<p>
Within the <code><b>settings.py</b></code> file

inside the <code>INSTALLED_APPS</code> area add these:

<code>
'signup',
'django.contrib.sites',
'allauth',
'allauth.account',
'allauth.socialaccount',
'allauth.socialaccount.providers.google',
</code>

add the <code>TEMPLATES</code>, <code>AUTHENTICATION_BACKENDS</code>, <code>SITE_ID = 1</code>, <code>SOCIALACCOUNT_PROVIDERS</code> scripts from the documentation <a href="https://django-allauth.readthedocs.io/en/latest/installation.html">documentation</a>

add the <code>LOGIN_REDIRECT_URL = '/'</code> at the end of the <code><b>settings.py</b></code> file
</p>

<h3>Create superusers</h3>
<p>
<code>$ python manage.py createsuperuser</code>
</p>

<h3>Django Commands</h3>
<ul>
    <li><code>$ python manage.py makemigrations</code></li>
    <li><code>$ python manage.py migrate</code></li>
    <li><code>$ python manage.py runserver</code></li>
</ul>

<h3>Create site</h3>
<p>
at the admin page/sites add site with domain 127.0.0.1:8000
</p>
<p>
and then set <code>SITE_ID = 2</code> inside <code><b>settings.py</b></code> file
</p>

<h3>Create simple tamplate</h3>
<p>
inside the app folder create an <code><b>index.html</b></code> file to override the default template of allauth package
</p>

<h3>urls.py</h3>
<p>

import: 
<code>from django.views.generic import TemplateView</code>
add to urlpatterns:
<code>path('', TemplateView.as_view(template_name='signup/index.html'))</code>
<code>path('accounts/', include('allauth.urls'))</code>

<h3>settings.py</h3>, <code>TAMPLETES</code> area, set:
<code>'DIRS': [os.path.join(BASE_DIR, 'tamplates')]</code>
</p>


<h3>GOOGLE CLOUD PLATFORM</h3>
<p>
<ul>
    <li>create a new project and give it a name</li>
    <li>go to API and services/credentials</li>
    <li>set consent screen to external and create</li>
    <li>create credentials and set ID Client OAuth</li>
    <li>take note of your client id and your secret key</li>
    <li>set application Type = Web Application</li>
    <li>add URI = http://127:0:0:1:8000</li>
    <li>add URI redirect = http://127:0:0:1:8000/accounts/google/login/callback/</li>
</ul>

<p>run the server and go to admin page</p>

<ul>
    <li>at admin/social applications add social applications</li>
    <li>set provider = Google</li>
    <li>insert your client id and your secret key</li>
    <li>add the sites created (127:0:0:1:8000)</li>
</ul>
</p>