# DER Físico – Plataforma de Fitness

```mermaid
erDiagram
    %% ==== RELACIONES PRINCIPALES ====
    USUARIO ||--o{ PERFIL : "tiene"
    USUARIO ||--o{ USUARIO_RUTINA : "sigue"
    RUTINA ||--o{ USUARIO_RUTINA : "seguida por"
    ENTRENADOR ||--o{ RUTINA : "crea"
    USUARIO ||--o{ PROGRESO : "registra"
    USUARIO ||--o{ USUARIO_PRODUCTO : "compra"
    PRODUCTO ||--o{ USUARIO_PRODUCTO : "comprado en"
    USUARIO ||--o{ RESEÑA : "escribe"
    ENTRENADOR ||--o{ RESEÑA : "recibe"
    RUTINA }o--|| CATEGORIA : "pertenece a"
    PRODUCTO }o--|| CATEGORIA : "pertenece a"
    USUARIO ||--o{ USUARIO_GRUPO : "pertenece"
    GRUPO ||--o{ USUARIO_GRUPO : "tiene"
    USUARIO ||--o{ ENTRENADOR : "puede ser"

    %% ==== TABLAS ====
    USUARIO {
        int id_usuario PK
        string nombre
        string email
        date fecha_nacimiento
    }

    ENTRENADOR {
        int id_entrenador PK
        int id_usuario FK
        string nombre
        string especialidad
        string certificaciones
        enum tipo_entrenador  "personal_trainer | nutricionista | otro"
    }

    PERFIL {
        int id_perfil PK
        int id_usuario FK
        float altura
        float peso
        string objetivos
        string preferencias
    }

    RUTINA {
        int id_rutina PK
        int id_entrenador FK
        string nombre
        int duracion
        string nivel_dificultad
        int id_categoria FK
    }

    USUARIO_RUTINA {
        int id_usuario FK
        int id_rutina FK
        date fecha_inicio
    }

    PROGRESO {
        int id_progreso PK
        int id_usuario FK
        date fecha
        float peso
        int repeticiones
        string notas
    }

    PRODUCTO {
        int id_producto PK
        string nombre
        string tipo
        decimal precio
        int id_categoria FK
    }

    USUARIO_PRODUCTO {
        int id_usuario FK
        int id_producto FK
        date fecha_compra
        int cantidad
    }

    RESEÑA {
        int id_resena PK
        int id_usuario FK
        int id_entrenador FK
        string contenido
        int calificacion
        date fecha
    }

    GRUPO {
        int id_grupo PK
        string nombre
        string descripcion
    }

    USUARIO_GRUPO {
        int id_usuario FK
        int id_grupo FK
    }

    CATEGORIA {
        int id_categoria PK
        string nombre
        string descripcion
    }
```

---

### Transformación

**Herencia resuelta con FK:**

- `ENTRENADOR.id_usuario` referencia a `USUARIO`.

**Relaciones N:M resueltas con tablas intermedias:**

- `USUARIO_RUTINA`, `USUARIO_PRODUCTO`, `USUARIO_GRUPO`.
- Cada una incluye FKs + atributos propios (por ejemplo, `fecha_inicio` para saber desde cuándo sigue la rutina).

**Relaciones 1:N:**

- `PERFIL.id_usuario` → un usuario puede tener varios perfiles (o uno según reglas).
- `RUTINA.id_entrenador` → una rutina la crea un entrenador.
- `RESEÑA.id_usuario` y `RESEÑA.id_entrenador` → se puede saber quién escribió y a quién va dirigida.

**CATEGORIA reutilizada**

- Tanto `RUTINA` como `PRODUCTO` se ligan a `CATEGORIA` vía FK → evita duplicar categorías.

**Nutricionista y Personal Trainer como tipo_entrenador**

- El campo  tipo_entrenador incluirá : personal_trainer | nutricionista | otro

