# Django-setup

'''
1.
Creat a database by logging into mysql
$ mysql -u root -p 
$ pswd: Abhilash
>>> craete databas core
>>> use core
>>> cntl + D
START --> a$ sudo mysql service start

2.
Install Python3, nginx, pip3
Using pip3, instal a virtualenv
a$ sudo -H pip3 install virtualenv
WITH PYTHON3 a$ virtualenv -p /usr/bin/python3.5 venv22
a$ source venv22/bin/activate
(venv22)$ pip3 install django==1.9.4
(venv22)$ python -m django --version
(venv22)$ django-admin startproject mysite
Install all the reqirements in req.txt file
(venv22)$ pip3 install -r req.txt
(venv22)$ 

(venv22)$ django-admin startproject mysite
(venv22) myproject $ python manage.py runserver 
(venv22) myproject $ python manage.py startapp polls
(venv22) myproject $ python manage.py runserver 
(venv22) myproject $ python manage.py migrate
    Now open python shell, add some data to models and migrate. Check ur database table
Till now I have models, database with some data (as it is a local project)

3.
Coming to Mobibooks, pulled the code, installed nginx, python3, using pip3 installed venv2, gunicorn (pip3 install gunicorn)

PATH: (venv2) abhilash@abhi:~/Documents/mobi'bBackend/a/MobiCore$
    Now $cd --> $ la .bash* --> deleete any swap files if present
                $ vu .bashrc --> add these files at the end i.e ENVIRONMENT VARIABLES 
                        export DB_ENGINE="django.db.backends.mysql"
                        export MYSQL_USER="root"
                        export MYSQL_PASS="Abhi"
                        export MYSQL_HOST="localhost"
                        export MYSQL_PORT=""
                        export BASE_DIR="/home/abhilash/Documents/mobi'bBackend/a/MobiCore"
    Go to settings.py(here multitenancy.py )of MobiCore to See/Update the database 

Check what database is connected to ur django project, 
    (venv2) $ python manage.py shell
    >>> from django.db import connection
    >>> db_name = connection.settings_dict['NAME']
    >>> db_name
    (venv2)$ python manage.py migrate #migrate the modes to database

4. Nginx and Gunicorn
Nginx
    #Setup/change nginx default file
    #abhilash@abhi:/etc/nginx/sites-enabled$ sudo vi defaul with our modifications and save
    #START --> cd $: sudo service nginx start --> to start nginx.
    #CHECK --> /etc/nginx$: sudo service nginx status --> to check the status of nginx
    #RELOAD--> /etc/nginx$: sudo nginx -s reload
Gunicorn
START --> (venv2)$ gunicorn -D -c gunicorn_config.py ACT.wsgi #START gunicorn 
CHECK --> (venv2)$ ps aux | grep gunicorn     #check whether gunicorn is working or not
RESTART --> (venv2)$ kill -HUP 13383 #To restart the server if we made any changes and again check with ps aux | grep gunicorn

Now access 127.0.0.1, I should get the login page of mobibooks
To chek whether 127.0.0.1 nginx is listening or not
root@abhi:/etc/nginx# netstat -tnlp | grep 80
5.   
    All logs present at :/var/log/nginx$ vi access.log
(venv2)$ 

10-05-2019
(venv2) abhilash@abhi:~/Documents/mobi'bBackend/a/MobiCore$
(venv2)$ tar unzip --> tar -xvzf something.tar.tgz

Mysql dumping
$ mysql -u root -p coreA < core.sql

dumps core.sql to coreA database (its like taking taking backup of core.sql ddb to a coreA db)
(venv2)$ 
(venv2)$ 
(venv2)$ 
(venv2)$ 


27-05-2019: Gir stash
git stash list, to list the stashes
git stash  --> to stash the current stats,
git statsh apply stash@{0} --> to apply a particular statsh
git stash apply --index --> to get the staged cmmits

'''
,


To fix ACT.log show issue
In ACT/settings.py change in logging ={}.
logging[handlers][level] = 'DEBUG'
logging[loggers][django][level] = 'DEBUG'
logging[loggers][act][level] = 'DEBUG'
