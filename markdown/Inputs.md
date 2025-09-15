# 🚀**Reporte de Practica Inputs en PHP y BD**

## INSTITUTO TECNOLOGICO SUPERIOR DE JALISCO

![logo](https://tse1.mm.bing.net/th/id/OIP.ALajFJwmiwuKqomOk1_1gwHaHa?rs=1&pid=ImgDetMain&o=7&rm=3)

## Nombre del Alumno:

### Jorge Alejandro Moreno González

## Materia:

### Programación Web

## Nombre del Maestro:

### Pedro Espinosa Esparza

## Carrera:

### Ing. Sistemas Computacionales.

## 🤖 Objetivo
#### A continuacion en este reporte, comprenderemos y aprenderemos algunos puntos importantes para poder conectar nuestra base de datos con el lenguaje PHP y sus servicios web. Asi tambien creando nuestra base de datos y codigo para fines de uso.

## Indice
- [¿Qué es un input en HTML?](#inputs)
- [Pasos para conectar a la base de datos](#instrucciones)
- [Resultados-Finales](#resultados-finales)

## 💭 Inputs
### ¿Qué es un input en HTML?
#### Un input en HTML es una etiqueta usada en formularios para que el usuario ingrese datos. Dependiendo de su atributo type, puede ser un campo de texto, contraseña, correo, número, archivo, botón, checkbox, radio, etc.

#### _Ejemplo de codigo_
```html
<!-- Campo de texto -->
<input type="text" name="usuario" placeholder="Escribe tu nombre">

<!-- Contraseña -->
<input type="password" name="clave">

<!-- Selección de correo -->
<input type="email" name="correo">

<!-- Subir archivo -->
<input type="file" name="avatar">

<!-- Opción seleccionable -->
<input type="radio" name="suscripcion" value="premium">
<input type="checkbox" name="intereses[]" value="deportes">

```

## 📖 Instrucciones
### _A continuación mostraremos los pasos necesarios para crear nuestra base de datos y nuestro codigo de PHP._

#### 1. Creamos nuestra base de datos con todos nuestros campos necesarios para poder almacenar toda nuestra informacion del formulario.
```sql
CREATE DATABASE formualario;

CREATE TABLE datos_formulario (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100),
  constraseña VARCHAR(100),
  email VARCHAR(100),
  telefono VARCHAR(20),
  sitioWeb VARCHAR(255),
  edad INT,
  fechaNacimiento DATE,
  satisfaccion INT,
  color VARCHAR(7),
  paises VARCHAR(50),
  ciudades VARCHAR(100),
  avatar_nombre VARCHAR(255),
  avatar_tipo VARCHAR(100),
  avatar_tamano FLOAT,
  intereses TEXT,
  suscripcion VARCHAR(50),
  fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 2. Creamos la conexion a nuestra base de datos y tambien verificamos que tenga conexion sin ningun problema.
```php
echo "<h1>Datos recibidos del formulario</h1>";

$servername = "localhost";
$username   = "root";
$password   = "";
$dbname     = "formulario";

// Crear conexión
$conn = new mysqli($servername, $username, $password, $dbname);

// Verificar conexión
if ($conn->connect_error) {
    die("Error de conexión: " . $conn->connect_error);
} else {
    echo "Conexión exitosa a la base de datos <br>";
}
```

#### 3. Este codigo nos ayuda a capturar los datos por medio de los inputs que tenemos en nuestro html y asi poderla almacenar en sus respectiva BD.
```php
// Capturar datos del formulario
$nombre = $_POST['username'] ?? null;
$contrasena = $_POST['password'] ?? null;
$email = $_POST['email'] ?? null;
$telefono = $_POST['phone'] ?? null;
$sitioWeb = $_POST['website'] ?? null;
$edad = $_POST['edad'] ?? 0;
$fechaNacimiento = $_POST['nacimiento'] ?? null;
$satisfaccion = $_POST['satisfaccion'] ?? 0;
$color = $_POST['color'] ?? null;
$paises = $_POST['paises'] ?? null;
$ciudades = $_POST['ciudades'] ?? null;
```

#### 4. En este caso para la subida de archivos, capturaremos con el siguiente codigo, ya que se captura de manera diferente para cada campo.
```php
// Procesar archivo subido
$avatar_nombre = $_FILES['avatar']['name'] ?? null;
$avatar_tipo   = $_FILES['avatar']['type'] ?? null;
$avatar_tamano = isset($_FILES['avatar']['size']) ? $_FILES['avatar']['size'] / 1024 : null;

```

#### 5. Lo mismo hacemos con los intereses, ya que son diferentes tipos de campos, como lo es el famoso **checkbox**, para seleccionar una opcion u otra o ambas.
```php
$intereses = isset($_POST['intereses']) 
    ? (is_array($_POST['intereses']) ? implode(", ", $_POST['intereses']) : $_POST['intereses']) : "No seleccionado";
$suscripcion = $_POST['suscripcion'] ?? null;
```
#### 6. Este campo es muy importante, porque tenemos una opcion para las contraseñas en php cuyo atributo es **password_hash**. Su funcion es encriptar la contraseña para que no se refleje en la base de datos como tal y asi evitar un robo de informacion importante.
```php
//Encriptamos la contraseña
$contrasena = isset($_POST['password']) ? password_hash($_POST['password'], PASSWORD_DEFAULT) : null;
```
#### 7. Insertamos ahora todos nuestros datos del formulario a nuestra base de datos, este codigo es muy similar a un codigo de base de datos cuando queremos insertar datos pero con comandos sql.
```php
// Insertamos en la base de datos
$sql = "INSERT INTO datos_formulario (
    nombre, constraseña, email, telefono, sitioWeb,
    edad, fechaNacimiento, satisfaccion, color, paises, ciudades,
    avatar_nombre, avatar_tipo, avatar_tamano,
    intereses, suscripcion
) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?)";
```
#### 8. Con este codigo se cumple la tarea de las **Consultas Preparadas** colocando las variables de php con su respectivo tipo de dato. 
```php
$stmt = $conn->prepare($sql);
$stmt->bind_param(
    "sssssisisssssdss",
    $nombre, $contrasena, $email, $telefono, $sitioWeb,
    $edad, $fechaNacimiento, $satisfaccion, $color, $paises, $ciudades,
    $avatar_nombre, $avatar_tipo, $avatar_tamano,
    $intereses, $suscripcion
);
```
#### 9. Imprimimos en nuestro formulario la confirmacion si se enviaron los datos o si hubo algun error en algun campo vacio, cerramos nuestra conexion a la BD.
```php
if ($stmt->execute()) {
    echo "<br><strong> Datos insertados correctamente en la base de datos.</strong>";
} else {
    echo "<br><strong> Error al insertar datos: </strong>" . $stmt->error;
}

$stmt->close();
$conn->close();
```

## 🌐 Resultados Finales 
#### Este es nuestro formulario con vista web (_Aun sin estilos CSS_)
![inputs](../html/imagenes/trece.png)
#### Agregamos datos adicionales para registrarlo a nuestra base de datos
![Insertar Datos](../html/imagenes/catorce.png)
#### Nos envia una confirmacion con nuestros datos ingresados, ahora revisamos nuestra BD
![confirmacion](../html/imagenes/quince.png)
#### Nuestros datos se registraron correctamente en nuestra BD, funcionando correctamente.
![confirmacion](../html/imagenes/17.png)

#### _Con este reporte hemos concluido nuestro aprendizaje el como funciona nuestro lenguaje PHP y como nos puede ayduar em manejar e insertar informacion en nuestras bases de datos._
