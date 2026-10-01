# Ejercicio 14 — Base de Datos de Gestión de Plataforma de Recetas Culinarias y Comunidad



Proyecto enfocado en la modelación Entidad-Relación (DER / MER) e implementación de base de datos relacional para una plataforma web/móvil de gastronomía y cocina comunitaria, administrando miembros registrados, publicación de recetas culinarias, pasos de preparación, catálogo de ingredientes con sus proporciones y sistema de reseñas/valoraciones.

---

## Descripción

El sistema modela una estructura de datos relacional para la gestión integral de una comunidad gastronómica. Permite el registro y perfilado de miembros, la publicación e historialización de recetas de cocina con sus instrucciones detalladas paso a paso, la vinculación de ingredientes necesarios mediante tablas de composición con cantidades de medida específicos, y el intercambio social mediante la emisión de reseñas, valoraciones con puntuación y comentarios entre usuarios.

---

## Funcionalidades e Implementación

### Entidades y Atributos

* Miembro:


* id_Mienbro: Clave primaria única identificadora del miembro o usuario de la plataforma.


* nombre: Nombre completo o identificador público del miembro.


* correo electronico: Dirección de correo electrónico asociada a la cuenta.


* tipo perfil: Rol o categoría del usuario dentro de la comunidad (ej. aficionado, chef profesional, administrador).


* fecha registro: Fecha en que se dio de alta el perfil en el sistema.




* Receta:


* id_codigo receta: Clave primaria identificadora de la receta culinaria.


* titulo: Título o nombre de la preparación culinaria.


* descripción: Resumen o reseña explicativa general del plato.


* tiempo preparación: Duración total o estimada requerida para la elaboración.


* dificultad: Nivel de complejidad de preparación (ej. fácil, intermedio, avanzado).


* porciones: Rendimiento o cantidad de raciones sugeridas de la receta.




* Paso:


* id_paso: Clave primaria identificadora de la instrucción o paso de la receta.


* numero_paso: Secuencia u orden numérico de ejecución (ej. Paso 1, Paso 2).


* descripción detallada: Explicación completa del procedimiento a seguir en esa etapa.


* tiempo estimado: Duración específica de esta fase de preparación.


* imagen: Enlace/URL o recurso gráfico representativo del paso.




* Ingrediente:


* id_codigo ingrediente: Clave primaria identificadora del ingrediente en el catálogo base.


* nombre: Nombre del insumo alimenticio (ej. Harina 000, Sal, Leche).


* categoria: Clasificación del insumo (ej. verduras, lácteos, especias, carnes).


* unidad medida: Unidad estándar por defecto de utilización (ej. gramos, tazas, mililitros, unidades).


* descripción: Notas adicionales o características del ingrediente.




* Receta_ingredientes:


* id_codigo receta: Clave foránea referenciando a la receta correspondiente.


* id_codigo ingrediente: Clave foránea referenciando al ingrediente requerido.


* cantidad: Proporción o monto específico necesario del ingrediente para la preparación de esa receta en particular.




* Reseñas:


* id_Mienbro: Clave foránea del usuario autor de la reseña.


* id_codigo receta: Clave foránea de la receta evaluada.


* puntuación: Calificación numérica asignada (ej. de 1 a 5 estrellas).


* comentario: Opinión, correcciones o feedback en texto redactado por el miembro.


* fecha publicación: Marca de tiempo del registro de la valoración.





---

## Relaciones del Modelo

1. Miembro ↔ Receta (Relación 1:N):


* Un miembro puede crear y publicar múltiples recetas dentro de la comunidad, pero cada receta pertenece a un único miembro autor.




2. Receta ↔ Paso (Relación 1:N):


* Una receta se compone de múltiples pasos secuenciales detallados, perteneciendo cada paso a una receta específica.




3. Receta ↔ Ingrediente (Relación N:M via Receta_ingredientes):


* Una receta utiliza múltiples ingredientes y, a su vez, un mismo ingrediente puede ser ingrediente de múltiples recetas. Esta relación de muchos a muchos se resuelve mediante la entidad asociativa `Receta_ingredientes`, detallando la `cantidad` utilizada.




4. Miembro ↔ Reseñas (Relación 1:N):


* Un miembro puede realizar múltiples valoraciones o reseñas sobre distintas recetas disponibles.




5. Receta ↔ Reseñas (Relación 1:N):


* Una receta puede recibir múltiples opiniones o puntuaciones enviadas por distintos miembros. La entidad `Reseñas` modela la interacción entre miembros y recetas.
