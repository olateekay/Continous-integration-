# Simulating a typical CI/CD Pipeline for a PHP Based application

In this project,we will be tasked with creating a pipeline that simulates continuous integration and delivery. We will have a `TODO` Web Applications are based on an interpreted (scripting) language (PHP). It means, it can be deployed directly onto a server and will work without compiling the code to a machine language.

The problem with that approach is, it would be difficult to package and version the software for different releases. And so, in this project, rather than downloading directly from git, we will be using Ansible `uri` module.

Target end to end CI/CD pipeline is represented by the diagram below.

![alt text](https://github.com/olateekay/Continous-integration-/blob/main/Images/image1.png)
