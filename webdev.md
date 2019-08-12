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
useful when combined with other front-end frameworks like ReactJS).
```
npm i express mongoose concurrently
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
