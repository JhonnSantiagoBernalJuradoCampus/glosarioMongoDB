# Mongo DB
## Bases de datos
1. Deberas ver primero que bases de datos tienes y usar la que necesites
- Para **ver las bases de datos** ejecutas el comando:
```js
show databases
```
- Para **usar** una base de datos en especifico ejecutas el comando:
```
use nombre_db
```
## Colecciones o tablas
1. Para **crear una coleccion** deberas ejecutar el comando:
```js
db.createCollection("nombre_tabla")
```
2. Para **ver las colecciones** que tienes ejecutas el comando:
```js
show collections
```
## Insertar datos
1. Para insertar datos en mongo db puedes hacerlo insertando uno solo o varios ejemplo
- Para insertar **un solo dato**:
```js
db.nombre_tabla.insertOne({
    nombre: "Santiago"
})
```
- Para insertar **varios datos** a la vez:
```js
db.nombre_tabla.insertMany([
    {
        nombre: "Ronald"
    },
    {
        nombre: "Angela"
    },
    {
        nombre: "Angie"
    }
])
```
# Operadores de comparación
- $eq
- $ne
- $gt
- $gte
- $lt
- $lte
- $in
- $nin
## $eq
Devuelve los datos que son ***igual que*** (**eq**ual). Por ejemplo: 
```js
{edad: {$eq: 20}}
```
Devolvera los datos donde la edad sea **igual a 20**
## $ne
Devuelve los datos que son ***distinto de*** (**n**ot **e**qual). Por ejemplo:
```js
{edad: {$ne: 30}}
```
Devolvera los datos donde la edad sea **distinta a 30**
## $gt
Devuelve los datos que son ***mayor que*** (**g**reater **t**han). Por ejemplo:
```js
{edad: {$gt: 15}}
```
Devolvera los datos donde la edad sea **mayor que 15**
## $gte
Devuelve los datos que son ***mayor o igual que*** (**g**reater **t**han or **e**qual). Por ejemplo:
```js
{edad: {$gte: 20}}
```
Devolvera los datos donde la edad sea **mayor o igual que 20**
## $lt
Devuelve los datos que son Menor que (**l**ower **t**han). Por ejemplo:
```js
{edad: {$lt: 40}}
```
Devolvera los datos donde la edad sea **menor que 40**
## $lte
Devuelve los datos que son ***menor o igual que*** (**l**ower **t**han or **e**qual). Por ejemplo:
```js
{edad: {$lte: 39}}
```
Devolvera los datos donde la edad sea **menor o igual que 39**
## $in
Devuelve los datos que se **esten** en el array especificado. Por ejemplo:
```js
{pais: {$in: ["Colombia", "Mexico"]}}
```
Devolvera los datos cuyo campo **pais** sea **Colombia** o **Mexico**
## #nin
Es la accion contraria a **$in**, devuelve los datos que **NO** esten en el array especificiado. Por ejemplo:
```js
{pais: {$nin: ["Colombia"]}}
```
Devolvera los datos cuyo campos pais **NO** sea Colombia
# Operadores de elemento
- $exists
- $type
## $exists
Comprueba que el campo existe. Por ejemplo:
```js
{genero: {$exists: true}}
```
Muestra los documentos donde existe un campo llamado **genero**
## $type
Comprueba el tipo del campo. Por ejemplo:
```js
{name: {$type: "string"}}
```
Muestra los documentos donde el campo name es de tipo **string**
# Operadores logicos
- $or
- $and
## $or
Filtra los documentos que cumplas alguna de las condiciones del array. Por ejemplo:
```js
{$or: [{edad: {$eq: 40}}, {edad: {$eq: 18}}]}
```
Muestra los documentos donde la edad sea igual a 40 o igual a 18
## $and
Similar a **$or** pero muestra los documentos que cumplan todas las condiciones del array y si no cumple alguna no lo muestra. Por ejemplo:
```js
{$and: [{nombre: {$ne: "Santiago"}}, {edad: {$gt: 20}}]}
```
Muestra los documentos donde el nombre no sea igual a **Santiago** y la edad sea mayor que **20**
# Update
- **updateOne** recibe como parametros la columna que se va a modificar en este caso lo hago por el **_id** y el dato que se va a enviar en el set:
```js
db.nombre_tabla.updateOne({_id: ObjectId("64c67c6fb06e1c6d173a1d3b")}, {$set: {nombre: "Santiago"}})
```
En este caso modifico la columna con _id *"64c67c6fb06e1c6d173a1d3b"* y le cambio su nombre a Santiago.

***Importante*** El updateOne solo actualiza el primer dato que encuentra con esa coincidencia.
- **updateMany**, es muy parecido a updateOne sin embargo este actualiza todos los datos que encuentre no solo el primero. Por ejemplo:
```js
db.nombre_tabla.updateMany({nombre: "Angie"},{$set: {nombre: "Angi"}})
```
Es este caso todos las columnas con nombre: **"Angie"** serán modificadas a Angi.
# Delete
- **deleteOne** Elimina la columna con la primera coincidencia. Por ejemplo:
```js
db.nombre_tabla.deleteOne({nombre:  "Santiago"})
```
Esto eliminara el dato con el nombre **"Santiago"**
- **deleteMany** Elimina todas las columnas con el parametro que coincide. Por ejemplo:
```js
db.nombre_tabla.deleteMany({nombre: "Angi"})
```
Esto eliminara todas las columnas cuyo nombre sea **"Angi"**