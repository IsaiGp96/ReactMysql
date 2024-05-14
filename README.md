# ReactMysql
Paso 1:
Cd BackEnd
npm init -y
npm install express mysql cors nodemon

Paso 2:
Copiamos lo siguiente en el archivo server.js
const express = require("express");
const mysql = require("mysql");
const cors = require("cors")

const app = express();
app.use(cors())

const db = mysql.createConnection({
    host: "localhost",
    user: "root",
    password: "root",
    database: "empleados",
})

app.get('/users',(re, res) => {
    const sql = "SELECT * FROM empleado";
    db.query(sql, (err, data) =>{
        if(err) return res.json(err);
        return res.json(data);
    })
})

app.get('/', (re, res) => {
    return res.json("Desde el Back End");
})

app.listen(8081, ()=>{
    console.log("Escuchando...")
})

Paso 3:
cd ..
cd frontEnd
npm i
npm run dev