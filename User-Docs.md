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

### Running and managing jobs

Get a list of jobs the authenticated user had submitted
```
agavepy.jobs.list(limit=250, offset=0)
```
Parameters:
* **limit**: The max number of results. (integer)
* **offset**: The number of records to when returning the results. When paginating results,the page number = ceil(offset/limit)(integer)

Response:
* Array of JobSummary object

#### JobSummary schema
```
{
  "$id": "http://agavepy.readthedocs.io/en/latest/JobSummary.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "properties": {
    "appId": {
      "description": "The unique name of the application being run by this job. This must be a valid application that the calling user has permission to run.",
      "type": "string"
    },
    "endTime": {
      "description": "The date the job ended in ISO 8601 format.",
      "type": "string"
    },
    "executionSystem": {
      "description": "The system id of the execution system.",
      "type": "string"
    },
    "id": {
      "description": "The unique id of the job.",
      "type": "string"
    },
    "name": {
      "description": "The name of the job.",
      "type": "string"
    },
    "owner": {
      "description": "The job owner.",
      "type": "string"
    },
    "startTime": {
      "description": "The date the job started in ISO 8601 format.",
      "type": "string"
    },
    "status": {
      "description": "The status of the job. Possible values are: PENDING, STAGING_INPUTS, CLEANING_UP, ARCHIVING, STAGING_JOB, FINISHED, KILLED, FAILED, STOPPED, RUNNING, PAUSED, QUEUED, SUBMITTING, STAGED, PROCESSING_INPUTS, ARCHIVING_FINISHED, ARCHIVING_FAILED",
      "type": "string"
    }
  },
  "required": [],
  "title": "AgavePy JobSummary schema",
  "type": "object"
}
```


