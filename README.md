# app-project-plan


## Goal

Goal is build a web application in a manner which most application are build in companies to understand the processes, tools and conventions that are usually in play. This means setting and configuring a github repo, setting up Continuous Integration and Continuous Deployment (CI/CD), using Infrastructure as Code (IAC), using a cloud platform (or alternatively hosting "on prem" on a seperate device, such as a raspberry pi, or old laptop), configuring a local development environment with docker (NIX is also fine but not as commonly used), database configuration and migration. The focus is not so much on the features of the app but instead on building and understanding the workflow. Having said that, we will focus on some vital parts of the application like Authentication as this is an important part of building web application.

The project plan will consist of two parts. The first part will be setting the whole workflow up and an app with the absolute minimum functionality so that we then can develop our application using Continuous Deployment.


## part 1: Setting the whole workflow up

### step 1: getting local environemnt working.

We are going to go for a standard stack that consists of a backend, a frontend and a relational database. To contain the 3 seperate parts and run a resuable and easy to manage local replica of our application we are going to use Docker and `docker compose`. Chose whatever langauge you want for backend, for frontend I suggest going with JS/TS and some common webframework like React/Svelte/Vue (there are so many... does not matter which you pick). As for relational database pick postgres or mysql. 

Lets start by creating a "User Registrating Flow". User will click a "Register" button, be taken to a register page where they will fill out a simple form and then submit, this form will be sent to a backend endpoint which will take the request and then reject returning[ Not Implemented Yet status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/501), webpage will display the error and do nothing more. I.e. we will setup a half-functioning registration flow as the absolute minimal functionality of our application.


### Step 2: setting up CI

Now that we have some simply functionality we need to setup some tests. Lets start by creating some simple unit test to test that the endpoint for registration exits at the path it should and can take requests and that it returns 501 status code.

Now we want that unittest to run in our CI. We will be using Github Actions to run our CI.

Our workflow in github for new features will be to make a Pull Request, review it and then merge it. Before merging PR should be allowed, the CI should pass. 

Configure a github action that runs unit tests on 

(Optional extenstion: running linting and code formatting in CI as well. Its very command that linting and formatting checks are run in CI as well. Linting is used to check syntax and to check unwanted use of code, and 


## part 2: Develop the app / add new features
