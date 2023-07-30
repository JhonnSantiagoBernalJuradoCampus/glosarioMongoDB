# Mongo DB
## Bases de datos
1. Deberas ver primero que bases de datos tienes y usar la que necesites
- Para ver las bases de datos ejecutas el comando:
```js
show databases
```
- Para usar una base de datos en especifico ejecutas el comando:
```
use nombre_db
```
## Colecciones o tablas
1. Para crear una coleccion deberas ejecutar el comando:
```js
db.createCollection("nombre_tabla")
```
2. Para ver las colecciones que tienes ejecutas el comando:
```js
show collections
```
## Insertar datos
1. Para insertar datos en mongo db puedes hacerlo insertando uno solo o varios ejemplo
- Para insertar un solo dato:
```js
db.nombre_tabla.insertOne({
    nombre: "Santiago"
})
```
- Para insertar varios datos a la vez:
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