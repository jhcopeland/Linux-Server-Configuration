# Linux-Server-Configuration
Project for Udacity course Fullstack Web Devloper

## Project Overview
A baseline installation of a Linux server was configured and prepared to host my web applications. The server has been secured from a number of attack vectors.  A databse server has also been installed and configured and I have deployed my catalog project to it that was created in a previous section of the course.


## User Requirements

1. Computer (Windows or MAC)
2. A terminal console program such as Git Bash to login to the server.
3. A web browser of your choosing to utilize the Catalog web application hosted on ther server.


## Server Details
- IP Address: 54.88.238.141
- SSH Port: 2200
- Remote Root Access = Disabled
- Timezone changed = UTC
- Apache installed and configured to serve a Python mod_wsgi application
- PostgreSQL installed and a database user = catalog configured with limited permissions
- Git installed
- Catalog Web Application project deployed and operating
- Key-based SSH authentication is enforced.
- Firewall (UFW) configured for SSH port 2200, HTTP port 80 and NTP port 123

### Server Login Instructions
1. Be sure you have obtained the provided user key from the reviewer notes and placed it in a local file.
2. Open a terminal console and enter the follwing: ssh grader@54.88.238.141 -p 2200 -i ~/(path to user key)/(user key filename)

### Installation and Configuration of Packages
- The following server commands were implemented to install and configure Python and Flask
  - sudo apt-get -qqy install python python-pip
  - sudo pip2 install --upgrade pip
  - sudo pip2 install flask packaging oauth2client redis passlib flask-httpauth
  - sudo pip2 install sqlalchemy flask-sqlalchemy psycopg2-binary bleach requests

- The following server commands were implemented to install and configure Apache and Python mod_wsgi
  - sudo apt-get install python-pip apache2 libapache2-mod-wsgi
  - sudo apt-get install apache2 apache2-utils libexpat1 ssl-cert python
  - sudo apt-get install libapache2-mod-wsgi
  - sudo /etc/init.d/apache2 restart

- The following server commands were implemented to install and configure PostgreSQL
  - sudo apt-get install postgresql postgresql-contrib

- The following server commands were implemented to install and configure Git
  - sudo apt-get update
  - sudo apt-get install git-core

- The following server commands were implemented to install and configure the Firewall (UFW)
  - sudo ufw default allow outgoing
  - sudo ufw default deny incoming
  - sudo ufw allow ssh
  - sudo ufw allow 2200/tcp
  - sudo ufw allow http
  - sudo ufw allow ntp
  - sudo ufw enable


## Catalog Web Application Details
- URL: http://54.88.238.141.xip.io

This is an application that performs the following:

- Provides a list of items within a variety of categories.
- Provides a user registration and authentication system.
- Registered users will have the ability to post, edit and delete their own items.

Specifically, this web application involves the use of a python program (application.py) to pull information from a PostgreSQL database for a catalog website.  This REST-ful web application uses the Python framework Flask along with a third-party OAuth authentication implementation to secure the database and various CRUD (create, read, update and delete) operations.  It also uses a third party "virtual" DNS implementation in order to utilize the OAUth authentication.

### The 3rd party providers are:
- Google OAuth 2.0 - This allows login to the web application
- xip.io for wildcard DNS - This is utilized to implement Google OAuth by prividing for a simulated DNS name for authorized Javascript Origin and paths for authorized redirect URIs.

### Catalog Web Application Instructions
1. Open your web browser and enter http://54.88.238.141.xip.io into the address bar.
2. If you're not already logged in, the application login screen will be displayed and prompt you to login.  (*All application functionality will be disabled until you login.*)
3. Once you are logged in, the home page will allow you to see the catalog, its catagories and associated items.
4. At this point you will be able to add, edit and delete items from the available catagories.
5. Select the logout button to log out of the application.
