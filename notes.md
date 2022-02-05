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
    and make sure you cd backend

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

****
Warning: Current Server Discovery and Monitoring engine is deprecated, and will be removed in a future version. To use the new Server Discover and Monitoring engine, pass option { useUnifiedTopology: true } to the MongoClient constructor.
    longer version of the same warning:
(node:38551) [MONGODB DRIVER] Warning: Top-level use of w, wtimeout, j, and fsync is deprecated. Use writeConcern instead.
(Use `node --trace-warnings ...` to show where the warning was created)
(node:38551) [MONGODB DRIVER] Warning: Current Server Discovery and Monitoring engine is deprecated, and will be removed in a future version. To use the new Server Discover and Monitoring engine, pass option { useUnifiedTopology: true } to the MongoClient constructor.
listening on port 3000

    I found this work around but I don't know where to insert it:
This works fine for me, and no more errors
https://github.com/Automattic/mongoose/issues/8156:
<script>
    mongoose
    .connect(process.env.MONGO_URI, {
    useUnifiedTopology: true,
    useNewUrlParser: true,
    })
    .then(() => console.log('DB Connected!'))
    .catch(err => {
    console.log(DB Connection Error: ${err.message});
    });
</script>

****
Know the differences:
post = create a new review
put = edit an existing review
delete = delete a review
****

node:38987) [MONGODB DRIVER] Warning: Top-level use of w, wtimeout, j, and fsync is deprecated. Use writeConcern instead.
in index.js
<script>
    wtimeout: 2500,
</script>
not sure how to fix this yet