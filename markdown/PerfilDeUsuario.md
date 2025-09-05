# 🚀**Reporte de Inputs Perfil de Usuario**

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

#### En este formato explicaremos el codigo por partes para identificar las etiquetas que fueron usadas para cada elemento.

##

#### Este codigo es un pequeño formulario utilizando 5 campos diferentes, los cuales fueron _text, password, email, tel y url_.

```HTML
<h1>Crear tu perfil de usuario</h1>
<form action="" method="">
  <fieldset>
    <legend>Informacion Basica</legend>
    <label for="username">Nombre de usuario:</label>
    <input
      id="username"
      type="text"
      name="username"
      placeholder="Escribe tu nombre"
      required
    /><br />
    <label for="password">Contraseña:</label>
    <input
      id="password"
      type="password"
      name="password"
      placeholder="Escribe tu contraseña"
      required
    />
    <br />
    <label for="email">E-mail:</label>
    <input
      id="email"
      type="email"
      name="email"
      placeholder="Escribe tu correo"
      required
    />
    <br />
    <label for="phone">Telefono:</label>
    <input
      id="phone"
      type="tel"
      name="phone"
      placeholder="Escribe tu telefono"
      required
    />
    <br />
    <label for="website">Sitio Personal:</label>
    <input
      id="website"
      type="url"
      name="website"
      placeholder="Escribe tu contraseña"
      required
    />
  </fieldset>
</form>
```

![prueba](../html/imagenes/uno.png)

##

#### Con este campo de tipo number, podemos solo ingresar datos numericos olvidando por completo el tipo texto.

```HTML
<fieldset>
        <legend>Informacion adicional</legend>
        <label for="edad">Tu edad:</label><br />
        <input type="number" name="edad" id="edad" />
        <br />
```

![prueba](../html/imagenes/Dos.png)

##

#### Con nuestro tipo de dato **_Date_** podemos ingresar una fecha que contenga dia, mes y año, en este caso como nuestra Fecha de Nacimiento

```HTML
<label for="nacimiento">Fecha de Nacimiento:</label><br />
        <input type="date" name="nacimiento" id="nacimiento" />
        <br />

```

![prueba](../html/imagenes/Tres.png)

##

#### El campo range nos ayuda a tener el rango en una pequeña barra de satisfaccion para indicar aproximadamente si es bajo o alto.

```HTML
<label for="satisfaccion">Nivel de satisfaccion:</label><br />
    <input
          type="range"
          min="1"
          max="99"
          name="satisfaccion"
          id="satisfaccion"
          />
        <br />

```

![prueba](../html/imagenes/cuatro.png)

##

#### Podemos incluso elegir nuestro propio color automaticamente o simplemente en el propio codigo seleccionando precisamente que color aparezca.

```HTML
<label for="color">Elige un color para tu perfil:</label><br />
        <input type="color" name="color" id="color" value="#ffffff" />
        <br />

```

![prueba](../html/imagenes/cinco.png)

##

#### Nuestra etiqueta **_option_** nos ayuda a obtener diferentes opciones como en este caso de paises, pudiendo seleccionar uno de ellos.

```HTML
<label for="paises">Selecciona un pais: </label><br />
        <select name="paises" id="paises">
          <option value="">-- Selecciona una opción --</option>
          <option value="mexico">Mexico</option>
          <option value="españa">España</option>
          <option value="argentina">Argentina</option></select>
          <br />

```

![prueba](../html/imagenes/seis.png)

##

#### Ahora es muy diferente a usar la etiqueta **_datalist_** ya que con ella podemos seleccionar y **modificar**, algo que en el codigo anterior no podemos hacerlo.

```HTML
<label for="ciudades">Selecciona una ciudad</label><br />
        <input
          list="lista-ciudades"
          id="ciudades"
          name="ciudades"
          placeholder="-- Escribe una ciudad --"
        />
        <datalist id="lista-ciudades">
          <option value="Lagos de Moreno"></option>
          <option value="Guadalajara"></option>
          <option value="Madrid"></option>
          <option value="Barcelona"></option></datalist>
          <br />

```

![prueba](../html/imagenes/siete.png)

##

#### Un campo importante y que usamos frecuentemente es el tipo de campo **_file_** que es para subir nuestros archivos desde nuestro dispositivo movil o computadora.

```HTML
<label for="avatar">Subir Foto</label><br />
        <input type="file" name="avatar" id="avatar" /><br />

```

![prueba](../html/imagenes/ocho.png)

##

#### **Checkbox** nos ayuda a elegir una opcion, otra opcion o las"dos juntas" teniendo la libertad de poder elegir cualquier opcion.

```HTML
<p>¿Que temas te interesan?</p>
        <input
          type="checkbox"
          name="intereses"
          id="tecnologia"
          value="tecnologia"
        />
        <label for="tecnologia">Tecnologia</label>
        <input
          type="checkbox"
          name="intereses"
          id="deportes"
          value="deportes"
        />
        <label for="deportes">Deportes</label>

```

![prueba](../html/imagenes/nueve.png)

##

#### Ahora tenemos un campo diferente lo cual es **radio**, solo podemos usarla como una opcion o la otra pero _no las dos juntas como el campo anterior_

```HTML
<p>Selecciona un nivel de suscripcion:</p>
        <input type="radio" name="suscripcion" id="basico" checked />
        <label for="basico">Basico</label>
        <input type="radio" name="suscripcion" id="premium" />
        <label for="premium">Premium</label>
        <br />
```

![prueba](../html/imagenes/diez.png)

##

#### Por ultimo tenemos tres botones con atributos diferentes, en este caso el boton **Registrar**: Nos almacena los datos ingresados en el formulario.

#### **Limpiar**: Practicamente limpia todo los datos ingresados.

#### **Boton Generico:** practicamente su uso no es algo muy importane para la programacion web, sin embargo suele utilizarse para usarse con etquetas "< a>" <a>vinculandolo hacia otro link.

```HTML
<input type="submit" value="Registrar" />
<input type="reset" value="limpiar" />
<input type="button" value="Boton Generico" />
```

![prueba](../html/imagenes/once.png)
