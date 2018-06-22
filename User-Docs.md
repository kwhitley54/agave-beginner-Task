# Agave - Beginner Documentation

Eager to get started? This page gives a good introduction on how to get started with Agave

Let's get started with the the turtorial.

### Installing Agave

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
### Buidling Images From a Dockerfile
Next, create a docker image that contains the python function and executes it as part of the default command. 

We can build images from a text file called a Dockerfile. You can think of a Dockerfile as a recipe for crating images. The instrusctions within a dockerfile either add files/folder to the images, add metadata to the image, or both.

#### The FROM instruction
we can use the `FROM` instruction to start our new image from a known image. this should be the first line of our Dockerfile.
```
FROM busybox
```
#### The ADD instruction
We can also add local files to our image using the `ADD` instruction. We can add a the file `Example.py` in our local directory to the `Users/kwhitley/PycharmProjects/Test` directory in our container with the following instruction:
``` 
ADD Example.py /Users/kwhitley/PycharmProjects/Test
```
The last step is write the command from running the application, which is simply- `python ./Example.py`. We use the `CMD` command to do that:
```
CMD ["python", "./Example.py"]
```
The primary purpose of `CMD` is to tell the container which command it should run when it is started. With that, our `Dockerfile` is now ready. This is what is looks like:
```
FROM busybox

ADD Example.py /Users/kwhitley/PycharmProjects/Test

CMD ["python", "./Example.py"]
```
Now that we have our `Dockerfile`, we can build our image. the `docker build` command does the heavy lifting of creating a Docker image from a `Dockerfile`.

The section below shows you the output of running the same.
```
Sending build context to Docker daemon  45.96MB
Step 1/3 : fROM busybox
 ---> 8c811b4aec35
Step 2/3 : ADD Example.py /Users/kwhitley/PycharmProjects/Test
 ---> Using cache
 ---> 94ef24d0d212
Step 3/3 : CMD ["python", "/Example.py"]
 ---> Using cache
 ---> b94a5737d86d
Successfully built b94a5737d86d
Successfully tagged python_example:latest
```

Congratulations! you have successfully created your first docker images

### Actors
Now that we going to register a docker container as an actor, to do this we have to an API client and once we have this you only have to do the set up once!

Do this excerise we are going to use a a python shell. the default python shell is python 2.7.5 but we want to use python 3.6.5

 To begin this excerise open your `Terminal`, once you have the terminal open type in the following:
```
Python3
```
This checks to see if you have python3 install in not please visit the pthon website(https://www.python.org).

Once you have the lastest python next you want to see if you have pip install. Similar to python the buildin version of pip is 2.7 but we want pip3 so you want to type in the follow:
```
pip3
```
if you dont have pip3 install use the following to install it:
```
sudo python3 get-pip.py
```

#### Pure Python

Authentication and authorization to the TACC Cloud APIs uses `OAuth2`_, a widely-adopted web standard. Our implementation of Oauth2 is designed to give you the flexibility you need to script and automate use of TACC Cloud while keeping your access credentials and digital assets secure.

This is covered in great detail in our Developer Documentation(http://developer.tacc.cloud/docs/abaco/developer-docs.html) but some key concepts will be highlighted here, interleaved with Python code.

The first step is to create a python object called `ag` pointing to an API server. Your project likely has its own API server, which are discoverable using the `tenants-list --rich` command in the TACC cloud CLI. for now, we can assume `api.tacc.utexas.edu(the default value) will work for you.

First, type in the following line in your shell:
```
>>> from agavepy.agave import Agave
```
Next, type in the following line in your shell:
```
>>> ag = Agave(api_server='http://api.tacc.utexas.edu')
```
Once the object is instantiated, interact with it according to the API documentation and your specific usage needs.

### Create a new Oauth client
```
>>> ag = Agave(api_server='https://api.tacc.utexas.edu',
...            username='your username',
...            password='your password')
>>> ag.clients.create(body={'clientName': 'enter a client name'})
```
You use the consumerKey and consumerSecret to generate Oauth tokens, which are temporary credentials that you can use in place of putting your real credentials into code that is scripting against the TACC APIs.

### Reuse an existing Oauth client
Once you generate a client, you can re-use its key and secret. Clients can be created using the Python-based approach illustrated above, via the TACC Cloud CLI `clients-create` command, or by a direct, correctly-structured ` POST` to the clients web service. No matter how you've created a client, setting AgavePy up to use it works the same way:
```
>>> from agavepy.agave import Agave
>>> ag = Agave(api_server='https://api.tacc.utexas.edu',
...            username='your username', password='your password',
...            client_name='my_client',
...            api_key='kV4XLPhVBAv9RTf7a2QyBHhQAXca',
...            api_secret='5EbjEOcyzzIsAAE3vBS7nspVqHQa')
```

