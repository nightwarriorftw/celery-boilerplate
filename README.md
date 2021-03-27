<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<br />
<p align="center">
  <a href="https://github.com/nightwarriorftw/celery-boilerplate">
    <img src="./public/img/django_celery_boilerplate_logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Celery Boilerplate</h3>

  <p align="center">
    This is a simple django celery boilerplate
    <br />
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## :beginner: About The Project

This is a simple django celery boilerplate.

### :wrench: Built With

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

#### Celery and Cronjob

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


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/nightwarriorftw/celery-boilerplate.svg?style=for-the-badge
[contributors-url]: https://github.com/nightwarriorftw/celery-boilerplate/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/nightwarriorftw/celery-boilerplate.svg?style=for-the-badge
[forks-url]: https://github.com/nightwarriorftw/celery-boilerplate/network/members
[stars-shield]: https://img.shields.io/github/stars/nightwarriorftw/celery-boilerplate.svg?style=for-the-badge
[stars-url]: https://github.com/nightwarriorftw/celery-boilerplate/stargazers
[issues-shield]: https://img.shields.io/github/issues/nightwarriorftw/celery-boilerplate.svg?style=for-the-badge
[issues-url]: https://github.com/nightwarriorftw/celery-boilerplate/issues
[license-shield]: https://img.shields.io/github/license/nightwarriorftw/celery-boilerplate.svg?style=for-the-badge
[license-url]: https://github.com/nightwarriorftw/celery-boilerplate/blob/master/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/developer-aman-verma
