
# Insertar Documentos

---

_Inserta un solo documento_


``` m
db.Alumnos.insertOne(
{
nombre:"Maximiliano"
 });
```
_Inserción de un documento mas complejo con Array_

```m
db.Alumnos.insertOne(
 {
   nombre: "Rosa",
   edad: 22,
   apellidos: "Cabeza de Vaca",
   aficiones: [ "Paracaidismo", "Lectura", "futbol"]
})
```

_Inserción de Documento con subdocumentos_

```m
db.Alumnos.insertOne(
{
    nombre: "Raul",
    edad: 67,
    cv: {
         "Informatica": "Bueno",
         "Marketing": "Bajo",
         "Contabilidad": "Medio"
        }
})
```
_Inserción de Documento con Id Personalizado_

``` m
 db.Alumnos.insertOne({ 
    _id: 1, 
    "Nombre":"Arcadia"
 }
)
 ```

_Insertar Multiples Documentos_

```m
  db.Alumnos.insertMany(
  [
   {
     _id:2,
     nombre: "Diana"
   },
   {
    _id:3,
    nombre: "Flor",
    edad: 43
   },
   {
    _id:4,
    nombre: "Francisco Jesus Uriel",
    edad: 34,
    aficion: "El agua Bendita",
    desgracia: "La ex"
   } 
   ]);
   ```


   