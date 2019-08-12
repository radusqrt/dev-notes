Building backend
----------------
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
