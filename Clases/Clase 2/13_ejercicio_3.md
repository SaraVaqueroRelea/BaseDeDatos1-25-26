# Ejercicio 3: Plataforma de Bienestar y Belleza

## 1. Lista predefinida de requisitos

1. Los usuarios pueden crear perfiles y seguir rutinas de ejercicio personalizadas.
2. Los entrenadores pueden publicar rutinas y consejos de bienestar.
3. Los usuarios pueden registrar su progreso en rutinas y metas de salud.
4. La plataforma ofrece productos de belleza y bienestar que los usuarios pueden comprar.
5. Los usuarios pueden hacer reseñas y valoraciones de productos y entrenadores.
6. Se pueden generar estadísticas de rendimiento y progreso personal.
7. Existen categorías de rutinas según objetivos: fuerza, cardio, relajación, belleza de piel, cuidado personal.
8. Los usuarios pueden unirse a grupos de interés para compartir consejos y retos.

---

## 2. Identificación de Entidades

* ​**USUARIO**​: persona que usa la plataforma para seguimiento de rutinas, productos y bienestar.
* ​**ENTRENADOR**​: persona que crea rutinas, consejos y programas de bienestar.
* ​**PERFIL**​: información personal, preferencias y objetivos de salud.
* ​**RUTINA**​: conjunto de ejercicios o actividades de bienestar.
* ​**PROGRESO**​: registro de avances y resultados de un usuario.
* ​**PRODUCTO**​: productos de belleza, suplementos o accesorios de bienestar.
* ​**RESEÑA**​: comentarios y valoraciones de productos o entrenadores.
* ​**GRUPO**​: comunidad de usuarios con intereses similares.
* ​**CATEGORIA**​: tipo de rutina o producto (fuerza, cardio, relajación, cuidado personal).

---

## 3. Identificación de Relaciones

* USUARIO–PERFIL: un usuario tiene un perfil (1:1).
* USUARIO–RUTINA: un usuario puede seguir varias rutinas (N:M).
* ENTRENADOR–RUTINA: un entrenador puede crear muchas rutinas (1:N).
* USUARIO–PROGRESO: un usuario registra múltiples progresos (1:N).
* USUARIO–PRODUCTO: un usuario puede comprar varios productos (N:M).
* USUARIO–RESEÑA: un usuario puede escribir varias reseñas (1:N).
* ENTRENADOR–RESEÑA: un entrenador puede recibir varias reseñas (1:N).
* RUTINA–CATEGORIA: cada rutina pertenece a una categoría (N:1).
* PRODUCTO–CATEGORIA: cada producto pertenece a una categoría (N:1).
* USUARIO–GRUPO: un usuario puede unirse a varios grupos y un grupo puede tener varios usuarios (N:M).

---

## 4. Identificación de atributos

| Entidad    | Atributos                                             |
| ------------ | ------------------------------------------------------- |
| USUARIO    | id\_usuario, nombre, email, fecha\_nacimiento         |
| ENTRENADOR | id\_entrenador, nombre, especialidad, certificaciones |
| PERFIL     | id\_perfil, altura, peso, objetivos, preferencias     |
| RUTINA     | id\_rutina, nombre, duracion, nivel\_dificultad       |
| PROGRESO   | id\_progreso, fecha, peso, repeticiones, notas        |
| PRODUCTO   | id\_producto, nombre, tipo, precio                    |
| RESEÑA    | id\_resena, contenido, calificacion, fecha            |
| GRUPO      | id\_grupo, nombre, descripcion                        |
| CATEGORIA  | id\_categoria, nombre, descripcion                    |

---

## 5. Jerarquías / Generalizaciones

* USUARIO (generalización) → puede ser ENTRENADOR o CLIENTE (usuario estándar).
* ENTRENADOR → puede ser PERSONAL\_TRAINER o NUTRICIONISTA.

