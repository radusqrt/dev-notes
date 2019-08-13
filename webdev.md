Building backend
================

Install dependencies
--------------------
```
npm init
```
- set entry point as ```server.js``` instead of the default ```index.js```
- set author and license (as MIT usually)

This results into a ```package.json```.

Install the backend framework ```express```, the database framework ```mongoose```
and ```concurrently``` in order to run more than one npm script at a time (could be
useful when combined with other front-end frameworks like ReactJS). ```mongoose``` need ```--save```
as well for future deploying on Heroku.
```
npm i express concurrently
npm i mongoose --save
```

Install ```nodemon``` as a dev-dependency (not needed for production) which
automatically updates the server every time we change the files.
```
npm i -D nodemon
```

Set up some starting scripts
----------------------------
In ```package.json``` add under ```scripts```:
```
"scripts": {
  ...
  "start": "node server.js",
  "server": "nodemon server.js"
}
```

Follow mern-shopping-list tutorial
----------------------------------
From now on just follow the existing base project [mern-shopping-list](https://github.com/radusqrt/mern_shopping_list).

Building frontend (with ReactJS)
================================

Install dependencies
--------------------

Create a new folder and a new ReactJS project.
```
mkdir client && cd client
create-react-app .
```

Install ```axios``` for future backend calls:
```
npm i axios
```

Set up some starting scripts
----------------------------
This is going to create a new ```package.json``` which is totally different from the first one.
In order not to write the whole link to ```http://localhost/``` every time we do a request,
we are going to add a ```proxy``` field into package.json.
```
{
  ...
  "proxy": "http://localhost:5000"
}
```

Add concurrent server & client scripts start in the backend ```package.json```.
Also, add client-install script.
```
{
  "scripts": {
    ...
    "client-install": "npm i --prefix client",
    "client": "npm start --prefix client", // prefix is used for going to the client dir
    "dev": "concurrently \"npm run server\" \"npm run client\""
  }
  ...
}
```

Reactstrap and Bootstrap
------------------------
```
cd client
npm i bootstrap reactstrap react-transition-group
```

Running issues
==============

If ```npm run dev``` has errors, apply:
```
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```
Prepare and deploy
==================

Add new script to your server ```package.json```:
```
{
  ...
  "scripts": {
    ...
    "heroku-postbuild": "NPM_CONFIG_PRODUCTION=false npm i --prefix client && npm run build --prefix client"
  }
}
```

Go to server folder (not client):
```
heroku login
heroku create
```
Go to [Heroku website](http://heroku.com) on your newly created app and click on **Deploy**.
After setting up git, ```git push heroku master``` and it should build and be available online.
