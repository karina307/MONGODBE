
# Reemplazar Documentos

## Sustituir un documento completo 

```m 
db.libros.replaceOne({_id:2},{titulo:'De la tierra a la luna', autor: 'Julio Verne', editorial:'Terra', precio:100})
```

# Borrar Documentos 

_Dos metodos_

1. deleteOne
1. deleteMany

**Eliminar todo el documento con un id = 2**
```m
db.libros.deleteOne({_id:2})
```

**Eliminar todos los documentos donde la cantidad sea mayoor a 150**
```m
db.libros.deleteMany({cantidad:{$gt:150}})
```

# Expresiones Regulares

**Seleccionar todos los documentos que contengan en el titulo una t**
```m
db.libros.find({titulo: /t/})
```

**Seleccionar todos los documentos donde en el titulo se encuentre la palabra JSON**

```m
db.libros.find({titulo:/JSON/})
```

**Seleccionar todos los documentos en donde el titulo  termine con la palabra tos**

```m
db.libros.find({titulo:/tos$/})
```

**Seleccionar todos los documentos en donde el titulo termine con una J**

```m
db.libros.find({titulo:/$J/})
```

## Operador $regex
**Seleccionar todos los documentos donde el titulo contenga la palabra para**

```m
db.libros.find({titulo:{$regex:'para'}})
```
```m
db.libros.find({titulo:{$regex:/para/}})
```

**Seleccionar todos los documentos donde el titulo contenga la palabra json pero que sea case sensitive**

```m
 db.libros.find({titulo:{$regex:/json/, $options: "i"}})
 ```

 **Seleccionar todos los documentos de la colección libros donde el titulo contenga la palabras tos al final y que sea case sensitive**

 ```m
 db.libros.find({titulo:{$regex:/tos$/, $options: "i"}})
 ```

 ## Ver solo ciertas Columnas

```m
 db.libros.find({},{titulo:1})
 ```

 **Seleccionar todos los documentos de la editorial planeta, pero mostrando solamente el titulo y la editorial**

```m
db.libros.find({editorial:'PLANETA'},{_id:0,titulo:1, editorial:1})
```
```m
 db.libros.find({editorial:{$regex:/PLANETA/, $options:"i"}},{_id:0,titulo:1, editorial:1})
```
### Operador exist
 _Permite buscar la existencia de una columna_

```m
db.libros.find({titulo:{$exists:true}})
```
```m
db.libros.find({titulo:{$exists:false}})
```

### Operador $type 
```m
db.libros.find({precio:{$type:16}})
```
```m
db.libros.find({precio:{$type:1}})
```
```m
db.libros.find({precio:{$type:'double'}})
```

## Tabla de tipos de datos de mongodb

|Type|Number|Alias|
|-|-|-|
|Double|1|"double"|


## Operador $set

Sirve para cambiar el valor de un campo dentro de la coleccion
```m
db.libros.updateOne({titulo:'Java como Programas'},{$set:{titulo:"Java como Programar"}})
```

**Actualizar el valor de la cantidad a 50 y el precio a 10 donde el id = 9**
```m
db.libros.updateOne({_id:9},{$set:{cantidad:50, precio:10}})
```

**Actualizar todos los documentos donde precio sea mayor a 10 por el precio a 150**

db.libros.updateMany({precio:{$gt:10}}, {$set:{precio:150}})

### Operador sort

**Ordenar todos los documentos de forma ascendente por la editorial y mostrar solamente titulo, precio y editorial**

```m
db.libros.find({}, {titulo:1, precio:1, editorial:1, _id:0}).sort({editorial:1})
```
```m
db.libros.find({}, {titulo:1, precio:1, editorial:1, _id:0}).sort({editorial:-1})
``` 

