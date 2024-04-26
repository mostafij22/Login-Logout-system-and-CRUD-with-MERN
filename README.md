
Backend run command: cd backend, nodemon index.js

Frontend run command: cd frontend , npm run dev


Backend Data flow:     Model ⇒ controller  ⇒ route ⇒ index.js(server)


Backend Set Up
=======================================


npm init --y

npm i express mongoose cors body-parser bcrypt jsonwebtoken dotenv nodemon 

server run command : nodemon index.js



.env
=====
PORT = 8000

MONGO_URL = mongodb+srv://mostafij:mostafij@cluster0.op3jh3p.mongodb.net/CRUD?retryWrites=true&w=majority&appName=Cluster0

            
            
index.js(Server)
=================================================================================

const express = require('express');

//=====Connect to Express app=====
const app = new express();




//=============Database Connection==============

const mongoose = require('mongoose');
const dotenv = require('dotenv');
dotenv.config();

const PORT = process.env.PORT || 7000;
const URL = process.env.MONGO_URL



mongoose.connect(URL).then(()=>{
    console.log("Database Connected Successfully");
    app.listen(PORT, ()=>{
        console.log(`Server is running on port: http://localhost:${PORT}`)
    })    
}).catch(error => console.log(error));




//=======Middleware import and implement======
  //--import--
    //===========
    const bodyParser = require('body-parser');
    const cors = require('cors');
      //--implement--
  //===========
  app.use(bodyParser.json());
  app.use(cors());
  


// Server Run Command: nodemon index.js

//==========Routing==============

//const userRoutes = require('./src/routes/userRoute');
//app.use('/api', userRoutes)




