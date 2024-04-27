# 🚀Jenkins X for Kubernetes

Jenkins is one of the most famous Continuous Integration tools and an integral part of DevOps that is often used to integrate various DevOps stages. Following the success of Jenkins, a new version of Jenkins has been introduced lately called Jenkins X (JX). It provides continuous integration, automated testing, and continuous delivery to Kubernetes.

## What is Jenkins X?
Jenkins X was first introduced by James Strachan (creator of Groovy, Apache Camel) in March 2018. It’s designed from the ground up to be a cloud-native, Kubernetes-only application that not only supports CI/CD but also makes working with Kubernetes as simple as possible. With one command you can create a Kubernetes cluster, install all the tools you’ll need to manage your application. You can also create build and deployment pipelines, and deploy your application to various environments.

Jenkins is described as an “extensible automation server” that is configured, via plugins, to be a Continuous Integration Server, a Continuous Deployment hub, or a tool to automate just about any software task. JX provides a specific configuration of Jenkins, meaning you don’t need to know which plugins are required to stand up a CI/CD pipeline. It also deploys numerous applications to Kubernetes to support building your docker container, storing the container in a docker registry, and deploying it to Kubernetes.

## Jenkins Vs Jenkins X

## Features of Jenkins X
 - ### Automated CI /CD:
Jenkins X offers a sleek jx command-line tool, which allows Jenkins X to be installed inside an existing or new Kubernetes cluster, import projects, and bootstrap new applications. Additionally, Jenkins X creates pipelines for the project automatically.

 - ### Environment Promotion via GitOps:
Jenkins X allows for the creation of different virtual environments for development, staging, and production, etc. using the Kubernetes Namespaces. Every environment gets its specific configuration, list of versioned applications and configurations stored in the Git repository. You can automatically promote new versions of applications between these environments if you follow GitOps practices. Moreover, you can also promote code from one environment to another manually and change or configure new environments as needed.

 - ### Extensions:
 It is quite possible to create extensions to Jenkins X. An extension is nothing but a code that runs at specific times in the CI/CD process. You can also provide code through an extension that runs when the extension is installed, uninstalled, as well as before and after each pipeline.

 - ### Serverless Jenkins:
 Instead of running the Jenkins web application, which continually consumes a lot of CPU and memory resources, you can run Jenkins only when you need it. During the past year, the Jenkins community has created a version of Jenkins that can run classic Jenkins pipelines via the command line with the configuration defined by code instead of the usual HTML forms.

 - ### Preview Environments:
 Though the preview environment can be created manually, Jenkins X automatically creates Preview Environments for each pull request. This provides a chance to see the effect of changes before merging them. Also, Jenkins X adds a comment to the Pull Request with a link for the preview for team members.
 
## How Jenkins X works?
The developer commits and pushes the change to the project’s Git repository.
JX is notified and runs the project’s pipeline in a Docker image. This includes the project’s language and supporting frameworks.
The project pipeline builds, tests, and pushes the project’s Helm chart to Chart Museum and its Docker image to the registry.
The project pipeline creates a PR with changes needed to add the project to the staging environment.
Jenkins X automatically merges the PR to Master.
Jenkins X is notified and runs the staging pipeline.
The staging pipeline runs Helm, which deploys the environment, pulling Helm charts from Chart Museum and Docker images from the Docker registry. Kubernetes creates the project’s resources, typically a pod, service, and ingress.
## Why Jenkins X?

Jenkins X automates your CI/CD processes, making them faster and more scalable. It is designed to take full advantage of Kubernetes, providing automatic setup of environments and deployments using modern practices like GitOps and preview environments.

## How to Install Jenkins X: A Quick Guide
 Installation of Jenkins X
In this section, I will show you how to install Jenkins X on Linux and Windows operating systems.

 1. **Linux:**
 
	To install (`jx`) on Linux, download the.tarfile, and unarchive it in a directory where you can run the (`jx`) command.

	1- Download thejxbinary archive usingcurland pipe (|) the compressed archive to thetarcommand:
```bash
curl -L "https://github.com/jenkins-x/jx/releases/download/$(curl --silent https://api.github.com/repos/jenkins-x/jx/releases/latest | jq -r '.tag_name')/jx-linux-amd64.tar.gz" | tar xzv "jx"
```
or, if you don’t have jq installed:
```bash
curl -L "https://github.com/jenkins-x/jx/releases/download/$(curl --silent "https://github.com/jenkins-x/jx/releases/latest" | sed 's#.*tag/(.*)\".*#1#')/jx-linux-amd64.tar.gz" | tar xzv "jx"
```
	2- Install the (`jx`) binary by moving it to a location in your executable path using themvcommand:

	3- Runjx --versionto make sure you're on the latest stable version

2. **Windows:**

	You can install it on Windows through Chocolatey. This is a third-party package management system that provides convenient one-step commands for local Jenkins X installations and upgrades.

Install the Chocolatey package management system using an Administrative Shell:

 1. Right-click menu: Start[Command Prompt (Admin)].
 2. At the shell prompt, execute a powershell.exethe command to download and install the choco binary and set the installation path so that the binary can be executed:
 ```bash
@"%SystemRoot%System32WindowsPowerShellv1.0powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object 
System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%chocolateybin"
```
 3. Install (`jx`) using Chocolatey:
```bash
choco install jenkins-x
```
You can update to the latest version of Jenkins X using Chocolatey:
```bash
choco upgrade jenkins-x
```
If you use scoop, then there is a manifest available.
	- To install the (`jx`) binary run:
```bash
scoop install jx
```
	- To upgrade the (`jx`) binary run:
```bash
scoop update jx
```
So that was all about the installation process.

## What to Expect Next?

After installation, you can start using Jenkins X to manage your projects:

- Create new projects or import existing ones into Jenkins X.
- Automatically setup CI/CD pipelines and preview environments for your applications.
- Monitor and manage the development lifecycle directly from your terminal or through a web interface.

