# Busquedas condicionales

# Operadores de Comparación 
   | Operador | Descripción | 
   | -- | -- |
   | $eq | igual |
   | $gt | Mayor que |
   | $gte | Mayor o Igual |
   | $in | Buscar un elemento en un array |
   | $lt | Menor que |
   | $lte | Menor o Igual |
   | $ne | Todos los elementos que no sean iguales |
   | $nin | Ninguno de los valores del arreglo |

## Busquedas

_Selecciona todos los documentos de una coleccion_
```m
db.libros.find()
db.libros.find({})
```

_Seleccionar todos los documentos de la coleccion libros donde la editorial sea Biblio_


```m
db.libros.find({editorial:'Biblio'})
```

_Seleccionar todos los documentos de la coleccion libros donde el precio sea igual a 25_

``` m
 db.libros.find({precio:25})
```

## Busquedas con operadores logicos

**Sintaxis**
```
{<columna>:{<operador>:<valor>}, ...}
```

_Seleccionar todos aquellos documentos de la coleccion libros donde el precio sea mayor a 25_

```m
db.libros.find({precio:{$gt:25}})
```

_Seleccionar aquellos documentos de la colección libros donde el precio se han mayores o iguales 20_

``` m 
db.libros.find({precio:{$gte:20}})
```
_Seleccionar aquellos documentos donde la editorial sea Biblio o Planeta_

```
db.libros.find({editorial: {$in:['Biblio', 'Planeta']}})
```

### Recuperar una sola fila

_Seleccionar aquellos documentos que sean biblio o planeta, pero mostrando solamente el primer documento encontrado_

```m
 db.libros.findOne({editorial:{$in:['Biblio', 'Planeta']}})
```

```m
db.libros.findOne({})
```

# Operadores lógicos 

| Operador | Descripción | 
| -- | -- |
| $and | Operador And. Devuelve los documentos que cumplen todas las condiciones |
| $or | Operador Or. Devuelve los documentos que cumplen alguna condición|
| $not | invierte el resultado de una condición |
| $nor | Devuelve los documentos que no cumplen las condiciones |
| $exist | Devuelve los documentos que tengan un campo concreto |
| $type | Selecciona los documentos si un campo pertenece a un tipo especifico |

### Operador AND

**Sintaxis:**
```m
db.coleccion.find({condicion1, condicion2})
```

```m
 db.coleccion.find({$and:[{condicion1}, {condicion2}]})
```

Seleccionar todos aquellos libros que valgan mas de 25 y cuya cantidad sea inferior a 15

```m
db.libros.find({precio:{$gt:25}, cantidad:{$lt:15}})
```

```m
db.libros.find({$and:[{precio:{$gte:25}},{cantidad:{$lt:15}}]})
```

```m
db.libros.find({$and:[{precio:{$gte:25}},{cantidad:{$lt:15}}, {editorial:{$eq:'Biblio'}}]})
```

### Operador OR

**Sintaxis:**

```m
 db.coleccion.find({$or:[{condicion1}, {condicion2}]})
```

Seleccionar todos aquellos libros que valgan mas de 25 o cuya cantidad sea inferior a 15

```m
db.libros.find({$or:[{precio:{$gte:25}},{cantidad:{$lt:15}}]})
```

### OR y AND Combinadas

Seleccionar los documentos de la editorial Biblio con precio mayor a 40 o libros de la editorial planeta con precio mayor a 30

```
 db.libros.find(
   {
       $or:[
         {$and:[{editorial:'Biblio'},{precio:{$gt:40}}]},
         {$and:[{editorial:'Planeta'},{precio:{$gt:30}}]}
         
         ]})
```      
      
      