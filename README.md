# MisRecursosApp

-------------------------------------------------------------------------------------------------------------------------------------------
- Descripción:

MisRecursosApp permite a los usuarios llevar un registro personalizado de sus series, películas y libros. Los usuarios pueden agregar, modificar, eliminar y consultar sus recursos favoritos, también filtrarlos y buscar por nombre. Esta aplicación está diseñada para organizar y hacer seguimiento del progreso y valoración de cada recurso.

-------------------------------------------------------------------------------------------------------------------------------------------
- Generalidades:

La base de datos está diseñada en MongoDB y consta de dos colecciones principales:
- Usuarios: almacena información de los usuarios registrados.
- Recursos: contiene los registros de series, películas y libros asociados a cada usuario.

- Cada recurso está relacionado con un usuario mediante el campo IdUsuario.
- Se implementan operaciones CRUD (Crear, Leer, Actualizar, Eliminar).
- Se pueden aplicar filtros por estado, formato y plataforma, además de una búsqueda por nombre del recurso.

-------------------------------------------------------------------------------------------------------------------------------------------
- Comandos para crear la base de datos y colecciones en MongoDB:
Ejecutar los siguientes comandos:


```
// Seleccionar o crear la base de datos:

use MisRecursosApp

// Crear las colecciones:

db.createCollection("Usuarios")
db.createCollection("Recursos")

// leer las listas:

db.recursos.find()

// Actualizar

db.recursos.updateOne(
  { _id: "id del recurso aca" },
  {
    $set: {
      nombre: "Nuevo nombre",
      genero: "Nuevo genero",
      plataforma: "Netflix",
      estado: "Abandonado",
      formato: "Película",
      fechaTerminacion: new Date("2025-06-05"),
      valoracion: 3,
      reseña: "Nueva reseña"
    }
  }
)

//Eliminar

db.recursos.deleteOne({ _id: "id del recurso aqui" })

//Filtrar por estado

db.recursos.find({ estado: "Abandonado" })

// por formato

db.recursos.find({ formato: "Libro" })

// por plataforma

db.recursos.find({ plataforma: "Apple TV" })

//Busquedas filtros

db.recursos.find({
  nombre: { $regex: "palabra_buscar", $options: "i" }
})

db.recursos.find({
  formato: "Película",
  plataforma: "Netflix",
  nombre: { $regex: "stranger", $options: "i" }
})
```
