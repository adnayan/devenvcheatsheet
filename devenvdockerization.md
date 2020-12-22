# Dockerize node environment

The aim of this text is to implement development environment dockerization with vscode as easy as possible. This development environment will work for any programming language for this walkthrough we will work on nodejs. Before starting, make sure you install [visual studio code](https://code.visualstudio.com/ 'Visual Studio Code'), [docker desktop](https://www.docker.com/products/docker-desktop 'Docker Desktop') and [Visual Studio Code Remote - Containers](https://code.visualstudio.com/docs/remote/containers 'Visual Studio Code Remote - Containers') plugin. Following are the list of technologies we are going to use.

1. Windows 10
2. Visual Studio Code
3. Docker Desktop
4. Visual Studio Code Remote - Containers

First, create a folder ".devcontainer" in the project root. Inside the ".devcontainer" folder create a file and named it "devcontainer.json". Paste the following code in the file.

```javascript
{
	// Environment identifier
	"name": "Nodejs Development Environment",
	// Name of the docker file
	"dockerFile": "Dockerfile",
	// Exposed ports
	"appPort": [8000],
	// Runtime arguments
	"runArgs": ["-u", "node"],
	// Setting object
	"settings": {
		"terminal.integrated.shell.linux": "/bin/bash"
	},
	// Command to run after creating the environment
	"postCreateCommand": "npm install",
	// Extensions
	"extensions": [
		"esbenp.prettier-vscode"
	]
}
```

A full list of properties are available in [this](https://code.visualstudio.com/docs/remote/devcontainerjson-reference 'devcontainer.json reference') link.

Now let's create a docker file inside ".devcontainer" folder and name it "Dockerfile". Inside the docker file paste the following lines and save.

```
FROM node:15.4.0-stretch
```

Finally, let's reopen the container by accessing the "Remote Containers" button located in the left bottom of the vscode and select "Remote-Containers: Reopen in Container" menu from the command pallet.

To check node version enter the following command in the terminal:

```
node -v
```

You are now able to run any scripts using npm command. For example, if you have a script to run a nodejs server in the package.json file as given below.

```javascript
{
  "name": "example-server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "node app.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

You can use "npm start" command to run it. And you can access the web application via localhost:port, for now we are using port 8000 (see devcontainer.json file above), so the application is available in the following url [http://localhost:8000/](http://localhost:8000/).
