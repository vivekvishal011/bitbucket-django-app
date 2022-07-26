**Edit a file, create a new file, and clone from Bitbucket in under 2 minutes**

When you're done, you can delete the content in this README and update the file with details for others getting started with your repository.

*We recommend that you open this README in another tab as you perform the tasks below. You can [watch our video](https://youtu.be/0ocf7u76WSo) for a full demo of all the steps in this tutorial. Open the video in a new tab to avoid leaving Bitbucket.*

---

## Prerequisites and Goals

We will be installing Django within a virtual environment. Installing Django into an environment specific to your project will allow your projects and their requirements to be handled separately.

## Installing the Packages from the Ubuntu Repositories

download and install all of the items we need from the Ubuntu repositories. We will use the Python package manager `pip` to install additional components a bit later.

need to update the local apt package index and then download and install the packages. The packages we install depend on which version of Python your project will use.

If you are using Django with Python 3, type:

sudo apt update
sudo apt install python3-pip python3-dev libpq-dev postgresql postgresql-contrib nginx curl

## Creating a Python Virtual Environment for your Project

you will be installing our Python requirements within a virtual environment for easier management.

you first need access to the `virtualenv` command. you can install this with pip.

If you are using Python 3, upgrade `pip` and install the package by typing:

sudo -H pip3 install --upgrade pip
sudo -H pip3 install virtualenv

With `virtualenv` installed, we can start forming our project. Create and move into a directory where we can keep our project files:

mkdir ~/django-demo
cd ~/django-demo

Within the project directory, create a Python virtual environment by typing:

``virtualenv vishalenv``

This will create a directory called `vishalenv` within your `django-demo` directory. Inside, it will install a local version of Python and a local version of `pip`. We can use this to install and configure an isolated Python environment for our project.

Before you install our project’s Python requirements, we need to activate the virtual environment. You can do that by typing:

``source vishalenv/bin/activate``

Your prompt should change to indicate that you are now operating within a Python virtual environment. It will look something like this: (vishalenv)user@host:~/django-demo$.

## Creating and Configuring a New Django Project

With our Python components installed, you can create the actual Django project files.

## Creating the Django Project

Since we already have a project directory, we will tell Django to install the files here. It will create a second level directory with the actual code, which is normal, and place a management script in this directory. The key to this is that we are defining the directory explicitly instead of allowing Django to make decisions relative to our current directory:

``django-admin startproject nitin ~/django-demo``

At this point, your project directory (~/django-demo in our case) should have the following content:

1. ~/django-demo/manage.py: A Django project management script.
2. ~/django-demo/nitin/: The Django project package. This should contain ``the __init__.py, settings.py, urls.py, asgi.py, and wsgi.py files.``
3. ~/django-demo/vishalenv/: The virtual environment directory we created earlier.

for more detail refer to this link:--https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-20-04

# Completing Initial app Setup

   ``python ./manage.py startapp myapp``
   
   for setting up myaap
   
   
    ``ls``
    
    to see the default file comes or not
    
    
   ``python ./manage.py migrate``
    ``python ./manage.py runserver``
    
    "for migrate and running of aap and it will browse on locallhost with port 8000"
    
    now use the git command to create local repo that will be git recognised:
    
    `git init`
    
    after that add the bitbucket repo to push everything via using this command:
    
    ``git remote add origin https://bitbucket.org/vivekvishal011/django-app/src/master/`` this for mine case
    
    then use git command for further process
    
    ``git add .``
    ``git commit -m "commit sms"``
    ``git push``
    
    now everything will be pushed to bitbucket repo that you have created.
    
    ``note:-- in case of error like fatal: refusing to merge unrelated histories
Error redoing merge 1234deadbeef1234deadbeef

then use this command it will solve this log 

``git pull origin branchname --allow-unrelated-histories``

now lets proceed for pipeline

from here we have two option either you can go to pipeline>>> choose pipeline>>>select the recommendaed >>and confirm or 
you can create a file with the name "bitbucket-pipelines.yml" and write the pipeline . both is gud but i choose own the 2nd one.

go to your terminal >>> create a file with teh name bitbucket-pipelines.yml >>> and write the pipeline and push it to your bitbucket repo

in my case the pipeline is 

<img width="814" alt="Screenshot 2022-07-26 at 4 55 53 PM" src="https://user-images.githubusercontent.com/88605079/180995089-e15d1ce7-b035-4e75-af7a-ea1454d32afb.png">

when you pushes this pipeline it will automatically trigger the bulid and deploy it to our s3 bucket of aws .


now from here you have two question how it recognise my aws account and rest of the variable that i used in the pipelines,right ??

the ans of the 1st question that is who it will recognise aws account 

for that either use aws cli or give the access to a/c by giving details in repo-settings of bitbucket or 

use ``aws configure`` command and then it will ask for access_id and secret_access_key provide both in terminal, it will get configured.

for more detail use this link:--https://bobbyhadz.com/blog/aws-cli-config-profile-could-not-be-found

answering the 2nd question i.e about variables::- for that you can give details of varibles by going to repo-settings in bitbucket >> deployment (left side bar) and give the varible in that appropriate stage in which you are performing the task.

note: this not much secure so for securing this on production we have to use aws-secret manager for more deatails 

use this link https://aws.amazon.com/secrets-manager/

if everything goes well then you will get the deployment successfull.


if not then you will face an isse telling about image failed lo load ??

to solve this just go to your pipeline and correct the image version like use as per your requirement or ask from devloper.
<img width="390" alt="Screenshot 2022-07-26 at 5 14 45 PM" src="https://user-images.githubusercontent.com/88605079/180998363-6e7b1103-1717-4fcd-98a9-4faf3fef468e.png">
 
 
 and sometimes may we failed cuz of wrong -pipe : verion using so write it with complete focus i.e 
 <img width="474" alt="Screenshot 2022-07-26 at 5 17 49 PM" src="https://user-images.githubusercontent.com/88605079/180998768-f4268e2c-6452-41d0-9e1e-875e67cef798.png">
 and always before pushing check the typo .
 
 what i made mistake is i type i s3 with small s . then i corrected it .



    
  ## project and file structure of django are given below :--



## Django Project Structure and File Structure

When we create a Django project, the Django itself creates a root directory of the project with the project name you have given on it. 
It contains the necessary files that would provide basic functionalities to your web applications. 

## Different files in Django Root Directory
`1. manage.py` 

This file is used as a command-line utility for our projects. 
you will use this file for debugging, deploying, and running our web applications.
The file contains the code for running the server, makemigrations or migrations, and several other commands as well.

There are several commands under manage.py. Few important ones are as follows:
`a. Runserver`

This command is used to start the test server for our web application, provided by the Django framework.

`b. makemigrations`

We use this command to apply new migrations across projects and apps that have been carried out due to the changes in the database.

`c. migrate`

This is the prior step of the makemigration command. We use this for making the changes to the modules in the database. 

<img width="472" alt="Screenshot 2022-07-26 at 2 23 38 PM" src="https://user-images.githubusercontent.com/88605079/180980313-45c03be4-4c15-484e-8adb-fdb0bdbdaf20.png">
---
---

## Project files

Project is the name you have given to your project while typing `django -admin startproject (project_name)`. In my case it is `NITIN`. It contains configuration files of the project.
<img width="884" alt="Screenshot 2022-07-26 at 3 37 19 PM" src="https://user-images.githubusercontent.com/88605079/180981305-7bc51279-873e-494f-a559-8dc85d67bba3.png">

``1. __init.py_``

The function of this file is to tell the Python interpreter that this directory is a package and involvement of this __init.py_ file in it makes it a python project.

``2. settings.py``

The setting.py is the most important file, and it is used for adding all the applications and middleware applications.

This contains several variable names, and if you change the value, your application will work accordingly.

It contains sqlite3 as the default database. We can change this database to Mysql, PostgreSQL, or MongoDB according to the web application we create.

It contains some pre-installed apps and middleware that are there to provide basic functionality.

![image](https://user-images.githubusercontent.com/88605079/180982168-f5c21883-8cb7-4c61-a75a-86b77bcdc617.png)


``3. urls.py``

URL is a universal resource locator, it contains all the endpoints that we should have for our website. It is used to provide you the address of the resources (images, webpages, websites, etc) that are present out there on the internet.

`this file tells Django that if a user comes with this URL, direct them to that particular website or image whatsoever it is.`

![image](https://user-images.githubusercontent.com/88605079/180982764-2c3b2216-8249-4527-97a1-adf65e12105f.png)

``4. wsgi.py``

WSGI stands for Web Server Gateway Interface, it describes the way how servers interact with the applications.

you just have to import middleware according to the server you want to use. For every server, there is Django middleware available that solves all the integration and connectivity issues.

![image](https://user-images.githubusercontent.com/88605079/180983230-6c9f1146-dbfd-49bd-bd5f-198f5b9777f4.png)

``5. asgi.py``

ASGI works similar to WSGI but comes with some additional functionality.  ASGI stands for Asynchronous Server Gateway Interface. It is now replacing its predecessor WSGI.

##Django Application Files

Django uses the concept of Projects and apps for managing the codes and presents them in a readable format. A Django project contains one or more apps within it, which performs the work simultaneously to provide a smooth flow of the web application. 

In the example of mine, I have created a Project named “nitin” and an App called “myapp”

Type the following command in the terminal:

         ``Python manage.py startapp myapp``
  
  ``Once the app is created, the following sub-files will be present under that app.``
  
  <img width="573" alt="Screenshot 2022-07-26 at 3 53 52 PM" src="https://user-images.githubusercontent.com/88605079/180984283-395911f7-7bd4-4886-89e2-f4b46d66bef7.png">


## `` NOTES:-- In my case project name is "nitin" and app name is "myapp" ``

``1.  _init_.py``

This file provides the same functionality as that in the _init_.py file in the Django project structure. It is an empty file and does not need any modifications. It just represents that the app directory is a package.

``2.  admin.py``

`Admin.py file is used for registering the Django models into the Django administration.`

It is used to display the Django model in the Django admin panel. It performs three major tasks:

a. Registering models

b. Creating a Superuser

c. Logging in and using the web application

We will learn more about the admin panel in the next article about Admin Interface.

``3. apps.py``

Apps.py is a file that is used to help the user include the application configuration for their app.

Users can configure the attributes of their application using the apps.py file.

``4. models.py``

Models define the structure of the database. It tells about the actual design, relationships between the data sets, and their attribute constraints. 

``5. views.py``

Views are also an important part when you talk about the Django app structure. Views provide an interface through which a user interacts with a Django web application. It contains all the views in the form of classes.

``6. urls.py``

Urls.py works the same as that of the urls.py in the project file structure. The primary aim being, linking the user’s URL request to the corresponding pages it is pointing to.

You won’t find this under the app files. We create this by clicking on the New file option written on the top, after the Project name.

``7. tests.py``

Tests.py allows the user to write test code for their web applications. It is used to test the working of the app.

``NOTES:--All the files we have discussed above are within every Django application you create. The main aim of these files is to provide you with backend support. 

 the settings.py and urls.py are the two main files we will be working with. Making changes to these files will bring unique functionalities to the web application you create.``
 
 ``FOR more detail read this article :---https://techvidvan.com/tutorials/django-project-structure-layout/``
 
 
 ## HAPPY BITBUCKETING!.....
 



















---

