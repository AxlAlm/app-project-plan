# app-project-plan


## Goal

Goal is build a web application in a manner which most application are build in companies to understand the processes, tools and conventions that are usually in play. This means setting and configuring a github repo, setting up Continuous Integration and Continuous Deployment (CI/CD), using Infrastructure as Code (IAC), using a cloud platform (or alternatively hosting "on prem" on a seperate device, such as a raspberry pi, or old laptop), configuring a local development environment with docker (NIX is also fine but not as commonly used), database configuration and migration. The focus is not so much on the features of the app but instead on building and understanding the workflow. Having said that, we will focus on some vital parts of the application like Authentication as this is an important part of building web application.

The project plan will consist of two parts. The first part will be setting the whole workflow up and an app with the absolute minimum functionality so that we then can develop our application using Continuous Deployment.


## part 1: Setting the whole workflow up

### step 1: getting local environemnt working.

We are going to go for a standard stack that consists of a backend, a frontend and a relational database. To contain the 3 seperate parts and run a resuable and easy to manage local replica of our application we are going to use Docker and `docker compose`. Chose whatever langauge you want for backend, for frontend I suggest going with JS/TS and some common webframework like React/Svelte/Vue (there are so many... does not matter which you pick). As for relational database pick postgres or mysql, but lets skip this for now!

To create a reusable and contained environment for our front- and backend we will use docker files and docker compose to run our application locally. Google around to learn more about docker and find some guide to setup docker for the language / framework you have chosen. The end result we are looking for is a workflow that looks like this:`

        1. when running `docker compose up` our front and backend is started in their seperate docker containers
        2. we can go to localhost:XXXX (any port is ok) to view our frontend
        3. we can go to localhost:XXXX (any port is ok) to access our backend
        4. when running `docker compose down` we tear down both containers


Lets now create a "User Registrating Flow" and make that work locally! User will click a "Register" button, be taken to a register page where they will fill out a simple form and then submit, this form will be sent to a backend endpoint which will take the request and then reject returning[ Not Implemented Yet status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/501), webpage will display the error and do nothing more. I.e. we will setup a half-functioning registration flow as the absolute minimal functionality of our application.


### Step 2: CI

Now that we have some simply functionality we need to setup some tests. Lets start by creating some simple unit test to test that the endpoint for registration exits at the path it should and can take requests and that it returns 501 status code.

Now we want that unittest to run in our CI. We will be using Github Actions to run our CI.

Our workflow in github for new features will be to make a Pull Request, review it and then merge it. Before merging PR should be allowed, the CI should pass. 

Configure a github action that runs unit tests on any push to a PR and make a rule in github that require PR to have all checks passed before merging is allowed.

(Optional extenstion: running linting and code formatting in CI as well. Its very command that linting and formatting checks are run in CI as well. Linting is to check the code for suspicious or unwanted usage that could or will lead to errors, and formatting ensures that all developers code look the same.)


### step 3: CD

Now we are going to setup some more github actions to deploy our application! Deplyoment of webapps can be very simple if one uses e.g. https://www.heroku.com/, https://render.com/ and https://fly.io/. But for the purpose of learing we will only be the absolute cheapest EC2 instance to host our stuff.

First, create an AWS account.

Then, lets pick a Infastructure as Code (IaC) tool to help us provising our resources! Suggestion is to use Terraform. For starters we need to configure terraform and then use it to create an instance of the cheapest EC2 for us!

If we are to host our application on a EC2 we need to setup some security, our own domain and probably some load balancing for good measure. 



## part 2: Develop the app / add new features
