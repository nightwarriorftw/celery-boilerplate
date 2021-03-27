
[![Open Issues](https://img.shields.io/github/issues/nightwarriorftw/celery-boilerplate?style=for-the-badge&logo=github)](https://github.com/nightwarriorftw/celery-boilerplate/issues) [![Forks](https://img.shields.io/github/forks/nightwarriorftw/celery-boilerplate?style=for-the-badge&logo=github)](https://github.com/nightwarriorftw/celery-boilerplate/network/members) [![Stars](https://img.shields.io/github/stars/nightwarriorftw/celery-boilerplate?style=for-the-badge&logo=reverbnation)](https://github.com/nightwarriorftw/celery-boilerplate/stargazers) ![Built with Love](https://img.shields.io/badge/Built%20With-%E2%99%A5-critical?style=for-the-badge&logo=ko-fi)![Maintained](https://img.shields.io/maintenance/yes/2021?style=for-the-badge&logo=github) ![Made with Python](https://img.shields.io/badge/Made%20with-Python-blueviolet?style=for-the-badge&logo=python)![Open Source Love](https://img.shields.io/badge/Open%20Source-%E2%99%A5-red?style=for-the-badge&logo=open-source-initiative) [![Follow Me](https://img.shields.io/twitter/follow/nightwarriorftw?color=blue&label=Follow%20%40nightwarriorftw&logo=twitter&style=for-the-badge)](https://twitter.com/intent/follow?screen_name=nightwarriorftw)

<br />
<p align="center">
  <a href="https://github.com/nightwarriorftw/celery-boilerplate">
    <img src="./public/img/django_celery_boilerplate_logo.png" alt="Logo" width="100" height="100">
  </a>

  <h3 align="center">Celery Boilerplate</h3>

  <p align="center">
    This is a simple django celery boilerplate
    <br />
  </p>
</p>

## :ledger: Index

- [About](#beginner-about)
- [Built](#wrench-built)
- [Installation](#nut_and_bolt-installation)
- [Credit/Acknowledgment](#star2-creditacknowledgment)
- [License](#lock-license)


## :beginner: About

This is a simple django celery boilerplate. 

Celery is a simple, flexible, and reliable distributed system to process vast amounts of messages, while providing operations with the tools required to maintain such a system.

It’s a task queue with focus on real-time processing, while also supporting task scheduling.

### :wrench: Built

Built using django, celery, rabbitMQ


### :nut_and_bolt: Installation

####  Virtual Environment
In this step we will setup a virtual environment. For this boilerplate project I have used **poetry** which is generally used for managing
packages of your project.

- Install poetry using this 
```
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3
```

- Setup the virtual environment
```
poetry env use python3.9
```

- Activate this virtual environment
```
source <path to your virtual env>/bin/activate
``` 
Generally, <path to the virtual env> is `/home/<username>/.cache/pypoetry/virtualenvs/<name of your virtual env>`

- Install requirements

While remaining inside source code root folder run :
```
poetry install
```

#### Setup RABBITMQ

```
sudo apt-get install rabbitmq-server`
sudo rabbitmqctl add_user myuser mypassword
sudo rabbitmqctl set_permissions -p / myuser ".*" ".*" ".*"
```

- Make sure that these celery configuration are added in your `settings.py` and update *myuser* and *mypassword* there

```
    BROKER_URL = 'amqp://myuser:mypassword@127.0.0.1:5672//'
    CELERY_ACCEPT_CONTENT = ['json']
    CELERY_TASK_SERIALIZER = 'json'
    CELERY_RESULT_SERIALIZER = 'json'
    CELERY_TIMEZONE = 'Asia/Kolkata'
    CELERY_IMPORTS = ('api.tasks',)
```

#### Makemigrations, migrate and run the server

```
python manage.py makemigrations
python manage.py migrate
```

#### Run server

```
python manage.py runserver
```

#### Celery

Open another terminal and run the following command 

```
celery -A celery_boilerplate worker -l info

```

Now in order to test open django shell `python manage.py shell` and run the following command

```
from fun_app.tasks import add
add.delay(10, 20)
```
Now you will observe the results in the terminal in which celery is running


## :star2: Credit/Acknowledgment
[Aman Verma](https://nightwarriorftw.netlify.app)
  - Github: [nightwarriorftw](https://github.com/nightwarriorftw)
  - Linkedin: [developer-aman-verma](https://linkedin.com/in/developer-aman-verma)
  - Twitter: [nightwarriorftw](https://twitter.com/nightwarriorftw)


Credits goes to me 
## :lock: License

[LICENSE](/LICENSE)
