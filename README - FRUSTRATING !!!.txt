# musician-app
NodeJS / React sample app for AWS CI/CD pipeline tutorial

https://www.youtube.com/watch?v=NwzJCSPSPZs

EC2 source dir : /var/app/current

=========================================================================

VERY FRUSTRATING THIS APP TOOK MY 2 DAYS AND GAVE ME LOTS OF ANXIETY

YOU CAN VIEW THIS https://github.com/utube2/musician-app/tree/master REPO WHICH I FORKED FROM https://github.com/jspruance/musician-app
.

Things to observe in the original state which is the first commit in both repos

1) no node_modules   ---- which is a good thing and i appreciate .

2) in the package.json

 "scripts": {
    "test": "jest",
    "start": "nodemon app.js", <------------------------ look this
    "start-dev": "nodemon app.js"
  },

so what happened my eb deployment thru code pipeline was failing  and i went crazy why.

then i figured out it needs Dockerfile ... but then again docker was working fine in the ec2 ..

but eb could not start the app with the docker file and kept failing n like i wasted 2 hours for this


then i made a tweak in the package.json and also in the Dockerfile which looks like
package.json


 "scripts": {
    "test": "jest",
    #"start": "nodemon app.js", ------------------------ >changed to|
    "start": " node app.js",    <-----------------------------------|
    "start-dev": "nodemon app.js"
  },

and in Dockerfile i change CMD ["node", "app.js"]

CMD ["npm","run","start"]
 

and wow it worked !!! but wait thats not the end later i realized most of the nodejs apps were working without Dockerfile
Twisteed init ?

so i observed couple of package.json and my recent came out fine, and then i finally i ran the code without the Dockerfile
yes without the Dockerfile , freaking crazy piece of shit waste of time but it worked!!!! 

