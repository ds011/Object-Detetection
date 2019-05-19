# Object-Detetection
**Object Identification for Patients with Amnesia**

*The objective of this project is to come up with a solution that would enable elder people suffering from memory loss to better navigate the location of their items.*


# Installation Instructions 

-  Clone the repo
	$ git clone https://github.com/deepanshurautela/Object-Detetection.git
	$ cd Object-Detetection

- Ensure that mysql server is up and running
- On Mac
  	$ brew install mysql
  	$ brew tap homebrew/services
  	$ brew services start mysql
  	mysqladmin -u root password 'yourpassword'

- Now install the requirements
	$ pip3 install -r requirements.txt 
	(This step will fail if mysql server is not running)

- Modify the settings.py file
  	$ cd project

### Make the following changes in the settings.py file 

- Modify the settings file by replacing it with your appropriate settings. 
		DATABASES = {
		    'default': {
		        'ENGINE': 'django.db.backends.mysql',
		        'NAME': '',
		        'HOST' : '',
		        'USERNAME' : '',
		        'PASSWORD' : ''
		    }
	    }

	    CLOUDINARY = {
  			'cloud_name': '',  
  			'api_key': '',  
  			'api_secret': '',  
		}

		AMQP_URI = {
    		'AMQP_URI': 'amqp://zqtfjfbn:tH8aOU7bVgzi0TDhIA0xAYd4lUyZ5pa2@mustang.rmq.cloudamqp.com/zqtfjfbn'
		}

- Make migrations 
	$ cd ..
	$ python3 manage.py makemigrations
	$ python3 manage.py makemigrations photo
	$ python3 manage.py migrate 

- Create a superuser 
	$ python3 manage.py createsuperuser

- Finally run the server 
	$ python3 manage.py runserver

- Now, open a Web browser and go to http://127.0.0.1:8000/. 

- Now in a second Terminal window 
	$ cd Object-Detetection/watson_part 
	$ nameko run detect --broker 
    'amqp://(Enter your credentials here)'


