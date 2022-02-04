# MERNstack-Restaurant-Reviews

original youtube tutorial at:
https://www.youtube.com/watch?v=mrHNSanmqQ4&t=0s

gitHub of original instructor Beau Carnes:
https://github.com/beaucarnes/restaurant-reviews

    npm init -y
    install express cors mongodb dotenv
    npm install -g nodemon

    add "type": "module", in package.json (after "main": "index.js")
follow other changes down below to get things to work 
    February 3, 2022

to start server:
    nodemon server

***Changes that I had to make to make this work so far***
matched json file found in github instructor
    https://github.com/beaucarnes/restaurant-reviews/blob/master/backend/index.js
***
change port 5000 to 3000
    localhost:3000/api/v1/restaurants
    (it works!!! yay! says hello world)
***
commented out in index.js:
    mongoose.set('useNewUrlParser', true);
    useNewUrlParse: true
because it is no longer supported even with downgrade in package json.
***
do not forget to add a .js to imports:
    import RestaurantsDAO from "../dao/restaurantsDAO.js";
    not
    import RestaurantsDAO from "../dao/restaurantsDAO";
it will not run and will not tell you why.
***
the database shows up but it is not "pretty" format. I'll have to check later how to fix that.
    http://localhost:3000/api/v1/restaurants