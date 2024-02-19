# SQL - Relaciones de Tablas y Operaciones

## Relaciones de Tablas en SQL

En SQL, las relaciones entre tablas son fundamentales para organizar y estructurar los datos. Hay tres tipos principales de relaciones:

### 1. Relación Uno a Uno (One-to-One)

En una relación uno a uno, una fila en una tabla está relacionada con exactamente una fila en otra tabla y viceversa. Para establecer una relación uno a uno, puedes usar una clave primaria y una clave externa.

Ejemplo de creación de tablas con relación uno a uno:

```sql
CREATE TABLE Empleados (
    empleado_id INT PRIMARY KEY,
    nombre VARCHAR(50)
);

CREATE TABLE Detalles_Empleado (
    detalle_id INT PRIMARY KEY,
    empleado_id INT UNIQUE,
    FOREIGN KEY (empleado_id) REFERENCES Empleados(empleado_id)
);
```

### 2. Relación Uno a Muchos (One-to-Many)

En una relación uno a muchos, una fila en una tabla puede estar relacionada con varias filas en otra tabla, pero una fila en la segunda tabla está relacionada con una sola fila en la primera tabla. Esto se logra mediante el uso de una clave primaria y una clave externa.

Ejemplo de creación de tablas con relación uno a muchos:

```sql
CREATE TABLE Departamentos (
    departamento_id INT PRIMARY KEY,
    nombre_departamento VARCHAR(50)
);

CREATE TABLE Empleados (
    empleado_id INT PRIMARY KEY,
    nombre VARCHAR(50),
    departamento_id INT,
    FOREIGN KEY (departamento_id) REFERENCES Departamentos(departamento_id)
);
```

### 3. Relación Muchos a Muchos (Many-to-Many)

En una relación muchos a muchos, varias filas en una tabla pueden estar relacionadas con varias filas en otra tabla. Esto se logra utilizando una tercera tabla, comúnmente llamada tabla de unión o intermedia.

Ejemplo de creación de tablas con relación muchos a muchos:

```sql
CREATE TABLE Estudiantes (
    estudiante_id INT PRIMARY KEY,
    nombre_estudiante VARCHAR(50)
);

CREATE TABLE Cursos (
    curso_id INT PRIMARY KEY,
    nombre_curso VARCHAR(50)
);

CREATE TABLE Inscripciones (
    estudiante_id INT,
    curso_id INT,
    PRIMARY KEY (estudiante_id, curso_id),
    FOREIGN KEY (estudiante_id) REFERENCES Estudiantes(estudiante_id),
    FOREIGN KEY (curso_id) REFERENCES Cursos(curso_id)
);
```

## Claves Primarias y Claves Foráneas

### Primary Key (Clave Primaria)

Una clave primaria es un campo o un conjunto de campos en una tabla cuyos valores son únicos para cada fila. La clave primaria se utiliza para identificar de manera única cada fila en la tabla.

Ejemplo de definición de una clave primaria:

```sql
CREATE TABLE Empleados (
    empleado_id INT PRIMARY KEY,
    nombre VARCHAR(50),
    salario INT
);
```

### Foreign Key (Clave Foránea)

Una clave foránea es una columna o un conjunto de columnas en una tabla que establece una relación entre dos tablas. La clave foránea se utiliza para vincular los datos de una tabla con los de otra.

Ejemplo de definición de una clave foránea:

```sql
CREATE TABLE Empleados (
    empleado_id INT PRIMARY KEY,
    nombre VARCHAR(50),
    departamento_id INT,
    FOREIGN KEY (departamento_id) REFERENCES Departamentos(departamento_id)
);
```

En este ejemplo, departamento_id en la tabla Empleados es una clave foránea que hace referencia a la columna departamento_id en la tabla Departamentos. Esto establece una relación entre las dos tablas.

## Operaciones en SQL

### JOIN

La operación JOIN se utiliza para combinar filas de dos o más tablas en función de una condición relacionada.

Ejemplo de JOIN:

```sql
SELECT Empleados.nombre, Departamentos.nombre_departamento
FROM Empleados
JOIN Departamentos ON Empleados.departamento_id = Departamentos.departamento_id;
```

### ALTER TABLE

La instrucción ALTER TABLE se utiliza para modificar una tabla existente, como agregar o eliminar columnas.

Ejemplo de ALTER TABLE (para agregar una columna):

```sql
ALTER TABLE Empleados
ADD COLUMN salario INT;
```

### INSERT INTO

La instrucción INSERT INTO se utiliza para agregar nuevas filas a una tabla.

Ejemplo de INSERT INTO:

```sql
INSERT INTO Empleados (nombre, departamento_id, salario)
VALUES ('Juan', 1, 50000);
```

### UPDATE

La instrucción UPDATE se utiliza para modificar los datos existentes en una tabla.

Ejemplo de UPDATE:

```sql
UPDATE Empleados
SET salario = 55000
WHERE empleado_id = 1;
```

### DELETE

La instrucción DELETE se utiliza para eliminar filas de una tabla.

Ejemplo de DELETE:

```sql
DELETE FROM Empleados
WHERE empleado_id = 1;
```

### DROP

La instrucción DROP se utiliza para eliminar una tabla o una base de datos completa.

Ejemplo de DROP (eliminar tabla):

```sql
DROP TABLE Empleados;
```
