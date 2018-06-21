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





