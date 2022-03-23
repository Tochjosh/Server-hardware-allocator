# Server resources calculator API

API Service backing client interfaces

## Technologies

- [Python 3.8](https://python.org) : Base programming language for development
- [Bash Scripting](https://www.codecademy.com/learn/learn-the-command-line/modules/bash-scripting) : Create convenient script for easy development experience
- [Django Framework](https://www.djangoproject.com/) : Development framework used for the application
- [Django Rest Framework](https://www.django-rest-framework.org/) : Provides API development tools for easy API development
- [Docker Engine and Docker Compose](https://www.docker.com/) : Containerization of the application and services orchestration

## Description

## Getting Started

Getting started with this project is very simple, all you need is to have Git and Docker Engine installed on your machine. Then open up your terminal and run this command `https://github.com/Tochjosh/Server-hardware-allocator.git` to clone the project repository.

Change directory into the project folder and build the base python image used for the project that was specified in **_dockerfile_** by running `docker-compose build`

Spin up other services needed for the project that are specified in **_docker-compose.yml_** file by running the command `docker-compose up`. At this moment, your project should be up and running with a warning that _you have unapplied migrations_.

Open up another terminal and run this command `docker-compose run web python server_calculator/manage.py makemigrations` for creating new migrations based on the models defined and also run `docker compose run web python server_calculator/manage.py migrate` to apply migrations.

In summary, these are the lists of commands to run in listed order, to start up the project.

```docker
1. git clone https://github.com/Tochjosh/Server-hardware-allocator.git
2. docker build (Note that you can skip this step and run the next command to automatically build and start the project)
3. docker-compose up
4. docker-compose run web python server_calculator/manage.py makemigrations
5. docker-compose run web python server_calculator/manage.py migrate
```
Once the project is up and running, you can access the api on your local browser through this [link](http://0.0.0.0:8000/details)


The initial view should look like this:


![Alt text](api_initial_view.png?raw=true "api view")


## Functionality

This api takes the properties of a server as an object, and also a list of object of properties of virtual machine as shown below:

Server type = {"CPU": 2, "RAM": 32, "HDD": 100}

Virtual Machines = [{"CPU": 1, "RAM": 16,"HDD": 10}, {"CPU": 1, "RAM": 16, "HDD": 10}, {"CPU": 2,"RAM": 32, "HDD": 100}]

Each element in the virtual machine list is a virtual machine with its required resources.

The API takes these objects, and uses a "first fit" algorithm to calculate the number of this type of server required to handle all the virtual machines optimally.

The image below shows a representation with the above server type and list of virtual machines with the calculated output:

![Alt text](api_test_view.png?raw=true "api view")


## Running Tests

Currently, truthy tests has been provided in each of the application defined in the project, before running the tests with the following command make sure that your api service is up and running.

```docker
docker-compose run web python server_calculator/manage.py test server_calculator

```

## License

The MIT License - Copyright (c) 2022
