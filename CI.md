# Simulating a typical CI/CD Pipeline for a PHP Based application

In this project,we will be tasked with creating a pipeline that simulates continuous integration and delivery. We will have a `TODO` Web Applications are based on an interpreted (scripting) language (PHP). It means, it can be deployed directly onto a server and will work without compiling the code to a machine language.

The problem with that approach is, it would be difficult to package and version the software for different releases. And so, in this project, rather than downloading directly from git, we will be using Ansible `uri` module.

Target end to end CI/CD pipeline is represented by the diagram below.

![alt text](image1.png)


## Set Up

This project will require a lot of servers to simulate all the different environments from `dev/ci` all the way to `production`

To get started, we will focus on these environments initially.

- Ci
- Dev
- Pentest

Throughout this project, tests will be carried out.

- `SIT` - System Integration Testing 
- `UAT` - User Acceptance Testing 

   NB: `SIT` and `UAT` do not require a lot of extra installation or configuration. They are basically the webservers holding our applications. 
- `Pentest` - Penetration testing. 
   
   `PENTEST` is where we will conduct security related tests, so some other tools and specific configurations will be needed. In some cases, it will also be used for Performance and Load testing. Otherwise, that can also be a separate environment on its own. It all depends on decisions made by the company and the team running the show.