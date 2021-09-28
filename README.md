# NODE EXPRESS API REST - PET SHOP PROJECT

## TUTORIAL STEP BY STEP

Hi!

I am Wilbur and I will accompany you during this Node JS tutorial!
We will create an API that will follow the REST standard and use Node JS, Express and MySQL to save our data.

In this API we will have several data, then we will be able to save our customer name service, the pet that will attend, the service performed, the status of this service, observations and the dates of the schedule and when it was saved in our database.

As our we will follow the REST standard, we will be able to create a semantic API with Get, Post, Put, Patch, Delete as well as we can better organize our code.We will use some LIBs, Controllers, Model and until the end of this tutorial we will have our API created from scratch.

Let's start?

----------------------------------------------------------------

We will need NodeJs to be installed on your machine.

We will also use the postman to consume our routes.

All ready? Let's start?

-------------------------------------------------- --------------

- ## Environments

Our JavaScript language in the backend, we need to prepare our environment and download the node on the official website.

We will click "Download" and we will have two options: "Current" that presents new features and other testing elements. The other version is "LTS" the latest stable version and Node support. We will use LTS and we will choose the operating system of our machine, which in this case will be Windows.

Finished the donwload, we will run the file. The installation is very simple, just accept the license terms and select the storage folder.

Once installation is complete, we will open the VSCOD and by finishing we will check that the Node was installed and its version. We will write the Node -V command to access this information. In the case of our project, the version used and v10.16.3.

To start our project in Node, we need a module manager, after all Node is nothing more than several modules. For this we will use NPM, or Node Package Manager

Node already installs NPM for us automatically, as we can check on the terminal by the NPM -V command, and its version. In this case we used 6.9.0.

To start the project we have an NPM command: NPM Init will be made several questions about our project as: package name (project name); Version; description; entry point (file that will boot the server. We do not yet have this file but it will be called index.js when we create the server); Test Command (we will not relieve tests in this tutorial); Git Repository; Keywords; author (our name); License (it's an open sole, so we're using the ISC license).

We confirm the information and a file named package.json has been created. This file will contain all information from our project, from the name, its version and scripts that can be performed until new packages that we can install.

We have a new Node project, but it still can not run, after all we do not have the Entry Point file.

----------------------------------------------------------------

- ## First Route

We are already the package.json, but we do not have the entry point.We will then create index.js, which will be responsible for running the server.To do so, we will use Express, a Node module that contains a library that will enable this execution with the server.

We will open the NPM website, in which we will look for the Express package.It is a framework that will help us create servers and routes.To install this package we will open our console and use the NPM Install Express command.After this, the packages will be installed and in our package.json file were created depending on the expression and its corresponding version, in the case at 4.17.1.

A series of Nodule modules have not been installed that we will not rise for production, and also the package-lock.json, the exact version that is running at this time on the server.

We can already use Express, and to call modulus within index.js We will write:

``` javascript
const express = require('express') 
```

We use a string because we refer to a library.Express will have multiple functions, and one of them is the application that will run on the server.We will also enter the port that the server should listen to access requests.This port will be 3000, and for now we will insert only one console.log () with a text message.

``` javascript
const express = require('express') 

const app = express()

app.listen(3000, () => console.log('servidor rodando na porta 3000'))
```

To run this server, in the console we will write the node index.js command.We will see the message 'server running on port 3000', as we expected.

If we access the browser the localhost path: 3000 we will have something running, but we can not find any get, after all we have not created any route yet.

In index.js add app.get () and we will request that a function is performed.Express has two elements that are returned: REQ, the request we receive and res, what we will send, what we want to render on the screen, for example.We will ask a message to be displayed on the screen.

``` javascript
const express = require('express') 

const app = express()

app.listen(3000, () => console.log('servidor rodando na porta 3000'))

app.get('/' (req, res) => res.send('Servidor rodando, tudo ok'))
```

Before the message is displayed in the browser, we need to overthrow the old server with "Ctrl + C" on the console, after all it is not updated alone.After this, we will run Node Index.js again.When we update the page, we will see the text message displayed when accessing the 3000 route.

Our application is a petshop agenda, so when someone is registering a service, such as a bath and tosa, we want all the necessary information saved.It does not make sense to create only one localhost.3000, we need to develop something that makes sense to our business.Therefore we will create the former and modify the text message.

``` javascript
const express = require('express') 

const app = express()

app.listen(3000, () => console.log('servidor rodando na porta 3000'))

app.get('/atendimentos', (req, res) => res.send('Você está na rota de atendimentos'))
```

When accessing LocalHost.3000 / AntiTiments we view the configured message.

----------------------------------------------------------------

- ## Using NODEMON

We commented at the beginning of the tutorial that we have some scripts that package.json inserts the project. For now we have only a test script that we will not use in this tutorial.

We will include a new scrip, the start, and then we can insert the command we want. Instead of obliging who is accessing the server to write node index.js and installation directory, we standardize that the start file will perform node index.js.

At this time, when we knock down the server we can simply enter NPM Start on the console, and the server will run. Insert the node index.js command within a script file is interesting because we will enter other commands besides startup server, and will save us a lot of time to rise and overturn servers all the time when we make a change.

It would be interesting that this update was automatic, but Node does not perform this alone, we would need a new library called Nodemon, which will work only in a development environment.

In the console we will write the Comand NPM Install - Save-dev Nodemon. After installation, we will have version 1.12.1 available in the project within Package.json in Devdependeices. Once the project is built for production they are not forwarded.

After this, in our Start script we no longer need to have node index.js, but nodemon index.js. In the console we will run the NPM ETERT, and to restart the servers we just need to activate the rs command.

The most interesting to use Nodemon is that we can change the response of the requisitions it will automatically restart our server, we will not have any action on the command line.

----------------------------------------------------------------

- ## Isolating the Express Config and Using Consign

We have our server running and receiving requests and rendering messages in the browser, and even for custom port / calls.

Our Index.js file runs multiple actions: Performs the server, listen to the port and manage the route of calls. It seems a bit disorganized.

We will create a new folder that we will call controllers, which will be responsible for organizing and managing the actions of our application. We will, within this folder a file called calls.js, is in it that we will control the route app.get.

We will withdraw the Route app.get of index.js and we will pass to service.js.

```Javascript
app.get('/atendimentos' (req, res) => res.send('Você está na rota de atendimentos'))
```

However, if we run again the door in the browser Nothing will be displayed, that is, calls.js stopped being recognized. This has occurred because we do not export this module (when we create separate files, we create modules).

First, we must export calls.js, and for this we will write mudule.Exports and then we will export the function that receives the app.

```Javascript
module.exports = app => { 

    app.get('/atendimentos' (req, res) => res.send('Você está na       rota de atendimentos'))
}
```

For now in the Attendance file.js set the call route and receiving the app. Therefore when we export this module, we export a function that performs this setting.

Even with this change, when we reload the browser will not yet be possible to find the route. Although we have exported, we do not use any content anywhere.

In our command line, we will install the consing when writing: NPM Install Consign. Consign will cluster all the routes that we are creating within the app.

As we perform with Express, we will import the module and then write in index.js:

```Javascript
const express = require('express') 
const consign = require('consign')

const app = express()

app.listen(3000, () => console.log('servidor rodando na porta 3000'))
```

To use CONSIGN in the right way, we will need to insert the Controllers folder and all the modules it contains so that they can be accessed by the APP.

We'll call Consign () and then we'll include all the DECONTROLLERS modules in App.

```Javascript
const express = require('express') 
const consign = require('consign')

const app = express()

consign()
    .include('controllers')
    .into(app)

app.listen(3000, () => console.log('servidor rodando na porta 3000'))
```

Now, when we update the browser, the route is already recognized and accessed. The whole new controller that we will be accessed directly, at the same time we have been able to better separate responsibilities and organize our code.

However, our Index.js file still has two responsibilities in the same file. Theoretically, the initial file should only rise the server, do not configure it.

To resolve this problem, we will create a new folder called Config, which will contain all contents regarding application settings.

Within this folder, we will create the CUSTOMEXPRESS.JS file. Here we will make some changes in Express before running it. We will withdraw the following index.js content and we will go to this new file:

```Javascript
const express = require('express') 
const consign = require('consign')

const app = express()

consign()
    .include('controllers')
    .into(app)
```

In this file we will also need to create a module.Exports and export a function, which in case will configure the application and will return to the App variable.

```Javascript
const express = require('express') 
const consign = require('consign')

module.exports = () => {
    const app = express()

    consign()
        .include('controllers')
        .into(app)

    return app

}
```

In index.js we will export CUSTOMEXPRESS, a function. We will still have to declare that Const App will be equal to CustomeXpress ()

```Javascript
const customExpress = require('./config/customExpress')

const app = customExpress()

app.listen(3000, () => console.log('servidor rodando na porta 3000'))
```

When we update the browser, we will check that everything operates normally. We have three files, and each of them has specific responsibilities.

----------------------------------------------------------------

``` javascript

```