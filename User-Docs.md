# Agave - Beginner Documentation

Eager to get started? This page gives a good introduction on how to get started with Agave

Let's get started with the the turtorial.

## Installing Agave

Installing Agave is very simmple, start by typing the following in your terminal:

Install from PYPI(https://pypi.org)):
```
pip install agavepy
```
## Make a Request
Now that you have Agave install, we are going to get started with Requests.

First, make sure that:

* Request is installed(http://docs.python-requests.org/en/master/user/install/#install)

* Request is up-to-date(http://docs.python-requests.org/en/master/community/updates/#updates)

Before we begin to making a request here is some addation information that couldbe useful.

The **Agave Platform** (http://agaveapi.co)) is an open source, science-as-a-service API platform for powering your digital lab. Agave allows you to bring together your public, private, and shared high performance computing (HPC), high throughput computing (HTC), Cloud, and Big Data resources under a single, web-friendly REST API.

* Run code
* Manage data
* Collaborate meaningfully
* Integrate anywhere

The purpose of this documentation is to help you build your own digital lab that allows you to:

* Launch a job
* Transfer a file/directory
* Update permission to share a file/directroy

Making a request with Request is very simple, begin by importing the Request module:

```
>>> import requests
```

Next, lets try to get a webpage. For example, let's get GitHub's public timeline:
```
>>> r = requests.get('http://api.github.com/events')
```
Now, we have a **Response** object called `r`. We can get all the information we need from this object.

Requests' simple API means that all forms of HTTP request are as obvious. 



