# 🚀**Reporte Galeria de Imagenes**

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
#### A continuacion en este reporte, aprenderemos a como diseñar nuestra propia galeria en base a codigo HTML y CSS, asi como un codigo importante que es **inline-block** que fui vista en clase precismante para tener una mejor flexibilidad en el acomodo de imagenes.

## Indice
- [Codigo paso a paso en HTML](#HTML)
- [JavaScript en HTML](#JavaScript)
- [Codigo de CSS](#CSS)
- [Resultados Finales](#Resultados)

## **HTML**

#### Este es nuestro encabezado iniciado con un section que sera como nuestr contenedor principal de todas las imagenes; Nuestras imagenes utilizando un onclick nos ayudara a seleccionar cada una de las imagenes, llamando su ID para poder realizar nuestra animación.

```HTML
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Galería</title>
</head>
<body>
    <section class="contenedor">
        <h2>Galeria de Imagenes</h2>
        <div class="galeria-inline">
            <img src="centroComercial.jpeg" alt="imagen1" onclick="openModal('modal1', 'imagen1')"" />
            <img src="centroComercial.jpeg" alt="imagen2" onclick="openModal('modal2', 'imagen2')" />
            <img src="centroComercial.jpeg" alt="imagen3" onclick="openModal('modal3', 'imagen3')" />
            <img src="centroComercial.jpeg" alt="imagen4" onclick="openModal('modal4', 'imagen4')" />
            <img src="centroComercial.jpeg" alt="imagen5" onclick="openModal('modal5', 'imagen5')" />
            <img src="centroComercial.jpeg" alt="imagen6" onclick="openModal('modal6', 'imagen6')" />
        </div>
    </section>
```

#### Nuestros contenedores *DIV* son uno para cada imagen donde se encuentran sus ID de cada imagen, su clase es dentro de un span ya que es la interacción que haremos en cada imagen.

```HTML
    <div id="modal1" class="modal">
        <span class="close" onclick="closeModal('modal1')">&times;</span>
        <img src="centroComercial.jpeg" alt="imagen1" class="modal-content">
    </div>

    <div id="modal2" class="modal">
        <span class="close" onclick="closeModal('modal2')">&times;</span>
        <img src="centroComercial.jpeg" alt="imagen2" class="modal-content">
    </div>

    <div id="modal3" class="modal">
        <span class="close" onclick="closeModal('modal3')">&times;</span>
        <img src="centroComercial.jpeg" alt="imagen3" class="modal-content">
    </div>

    <div id="modal4" class="modal">
        <span class="close" onclick="closeModal('modal4')">&times;</span>
        <img src="centroComercial.jpeg" alt="imagen4" class="modal-content">
    </div>

    <div id="modal5" class="modal">
        <span class="close" onclick="closeModal('modal5')">&times;</span>
        <img src="centroComercial.jpeg" alt="imagen5" class="modal-content">
    </div>

    <div id="modal6" class="modal">
        <span class="close" onclick="closeModal('modal6')">&times;</span>
        <img src="centroComercial.jpeg" alt="imagen6" class="modal-content">
    </div>
```

## 📖 **JavaScript**
#### Nuestro pequeño de codigo *JavaScript* solamente nos ayudara a la animacion por parte de nuestra galeria de imagenes al momento de hacer un click en cada una de ellas para mostrarnos nuestra foto en tamaño grande y animacion.
**NOTA: este codigo esta dentro de un script y se encuentra dentro del codigo HTML**

```javascript
    <script>
    function openModal(modalId, caption) {
        let modal = document.getElementById(modalId);
        modal.style.display = "flex";
        modal.classList.add("show");
        let message = modal.querySelector(".caption");
        message.innerText = caption;
    }

    function closeModal(modalId) {
        let modal = document.getElementById(modalId);
        modal.classList.remove("show");
        setTimeout(function () {
            modal.style.display = "none";
            modal.querySelector(".caption").innerText = "";
        }, 300);
    }
    </script>

```

## **CSS**
#### Este es nuestro codigo *css* para agregar nuestras imagenes y poder tener nuestro contenedor centrado pero con la finalidad de agregar animaciones en el.
```css
    * {
        box-sizing: border-box; /*controla el tamaño sumando magin, padding*/
    }

    body {
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        width: 100%;
        max-width: 1000px;
        margin: 0 auto;
    }

    h2 {
        text-align: center;
        font-size: 1.5rem;
    }

    .contenedor {
        padding: 80px 20px;
    }

    .galeria-inline img{
        display: inline-block;
        width: 270px;
        height: 160px;
        transition: transform 0.5s ease;
    }

    .galeria-inline {
        text-align: center;
    }

    .galeria-inline img:hover {
    transform: scale(1.05);
    cursor: pointer;
    }
```

#### Con este codigo sacado de la pagina de [W3 schools Responsive Modal Images](https://www.w3schools.com/css/css3_images_modal.asp) nos ayudara a poder agregar las animaciones como se muestra en sus imagenes de prueba y asi luzca bonito neustro diseño.

```css
.modal {
  display: none;
  position: fixed;
  z-index: 1000;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  align-items: center;
  justify-content: center;
  transition: opacity 0.5s ease;
}

.modal-content {
  position: relative;
  width: 90%;
  height: auto;
  max-width: 90%;
  max-height: 90%;
  border-radius: 5px;
  overflow: hidden;
  animation: zoomIn 0.5s;
}

@keyframes zoomIn {
  from {transform: scale(0.6);}
  to {transform: scale(1);}
}

.modal.show {
  display: flex;
  opacity: 1;
}

.close {
  position: absolute;
  top: 10px;
  right: 15px;
  color: #ffffff;
  font-size: 35px;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.3s;
}

@media screen and (max-width: 768px) {
  .galeria-inline {
    width: calc(50% - 20px);
  }
}

@media screen and (max-width: 480px) {
  .galeria-inline {
    width: calc(100% - 20px);
  }
}
```

## **Resultados**
#### Asi se muestra nuestra galeria de imagenes que en este caso solo utilice una para hacer la prubea, con sus respectivas animaciones.
![Galeria](../html/imagenes/18.png)
![Animacion](../html/imagenes/19.png)



#### _Con este reporte hemos concluido nuestro aprendizaje el como funciona nuestro lenguaje PHP y como nos puede ayduar em manejar e insertar informacion en nuestras bases de datos._