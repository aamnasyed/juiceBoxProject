### Subroutes with Express Router 
- make a folder of Routes with included subroutes 
- import express 
    - const express = require("express"); 
    - const Router = express.Router;
    OR 
    - const appRouter = require("express").Router(); // CREATE ROUTER 
    - Build It, Exort It, Import It, Attach It

- app.use((req, res, next ) => {
    res.send()
})

- app.get

- app.post


### bodyParser and Advanced Curl
- bodyParser is part of the express package 
- sending and receving data 
    - const bodyParser = require("bodyParser"); 
    - server.use((req, res, next) => {
        console.log("body is now", req.body)
    })
- bodyPaser takes something from the incoming body and turns it into an object 

### INtroduction to JSON WEB TOKENS
- const jwt = require('jsonwebtoken')
- jwt.verify()

- const SECRET_INGREDIENT = "krabby patty"

        - function encodeData (data) {
            const encoded = jwt.sign(
                data, 
                SECRET_INGREDIENT
            );
            return encoded;
        }

        function decodeData(encodeData) {
            const data = jwt.verify(
                encodedData, 
                SECRET INGREDIENT
            );
            return data;
        }

- GET /posts --> See posts
- POST /posts --> create post 
- PATCH /posts/:id --> update post 
- DELETE /posts/:id --> deactivate post 

### General
- what does curl do? 


### DOCUMENT NOTES
POST /api/users/register
POST /api/users/login
DELETE /api/users/:id

GET /api/posts
POST /api/posts
PATCH /api/posts/:id
DELETE /api/posts/:id

GET /api/tags
GET /api/tags/:tagName/posts

TALAL's CODE: 
async function getUserByUsername(username) {
    try {
      const { rows} = await client.query(`
        SELECT *
        FROM users
        WHERE username=$1;
      `,[username]);
      console.log("This is the getUserByUsername function");
        console.log(rows[0]);
      
      
      if(rows.length){
        console.log("user already exists");
        rows[0].posts = await getPostsByUser(rows[0].id);
        return rows[0];
      }else{
        return undefined;
      }
    //   return ;
    } catch (error) {
      throw error;
    }
  }
    
    https://github.com/Talal-mahmoudi/JuiceBox 