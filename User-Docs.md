# Agave - Beginner Documentation

Eager to get started? This page gives a good introduction on how to get started with Agave

Let's get started with the the turtorial.

## Installing Agave

Installing Agave is very simmple, start by typing the following in your terminal:

Install from PYPI(https://pypi.org)):
```
pip install agavepy
```
The agavepy package is a complete Python binding for TACC’s Agave API. Here, we can create a docker image that contains the python function and executes it as part of the default command.

Now, that we have the Agavepy package install, lets create a docker image that contains the python function and executes it as part of the default command. First create a python fine called `Example.py` and paste the sample code below in it.
```
def string_count():
    message = "Hey my name is john"
    words = message.split(' ')
    word_count = len(words)

    print('Number of words is: ' + str(word_count))

string_count()
```
Next, create a docker image that contains the python function and executes it as part of the default command. 
```
FROM busybox
ADD Example.py /Users/kwhitley/PycharmProjects/Test

CMD ["python", "/Example.py"]
```







