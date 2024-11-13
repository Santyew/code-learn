# <img src=../../../../images/coding-book.png width="40"> Code & Learn (Entornos de Desarrollo: Elaboración de diagramas de comportamiento)

## Tipos de Diagramas UML

1. **Diagramas Estructurales**
   - Representan la estructura estática del sistema.
   - Ejemplos: Diagrama de Clases, Diagrama de Componentes, Diagrama de Despliegue.

2. **Diagramas de Comportamiento**
   - Representan el comportamiento dinámico del sistema.
   - Algunos de estos diagramas son: ___Diagrama de Casos de Uso, Diagrama de Secuencia___, Diagrama de Colaboración, __Diagrama de Actividad__, Diagrama de Estado.

---

## 1. Diagrama de Casos de Uso

### Campo de Aplicación

- Se utiliza para capturar y definir los requisitos funcionales de un sistema.
- Ideal para identificar cómo los usuarios (actores) interactúan con el sistema y los objetivos que desean alcanzar.

### Componentes

- **Actores**: 
  - Entidades externas que interactúan con el sistema (usuarios, otros sistemas).
  - Pueden ser humanos, sistemas externos, o dispositivos.

- **Escenario**: 
  - Una descripción específica de cómo un actor interactúa con el sistema para lograr un objetivo.
  - Puede incluir pasos y condiciones.

- **Relación de Comunicación**:
  - Conexiones entre actores y casos de uso que muestran cómo interactúan.
  - Puede ser de tipo `include`, `extend` o relaciones generales.

### Ejemplo

```plaintext
                    +---------------------------+
                    |   Sistema de Biblioteca    |
                    +---------------------------+
                      /|\                    |
                       |                     |
                       |                     |
       +----------------------------+        |        +--------------------+
       |       Usuario               |        |        |    Administrador   |
       +----------------------------+        |        +--------------------+
             |                                |               |
             |                                |               |
+---------------------+              +--------------------+   |    +---------------------------+
|    Buscar Libros    |              |  Añadir Libros     |<---+--->|    Eliminar Libros         |
+---------------------+              +--------------------+        +---------------------------+
             |
             |
+---------------------+
|  Pedir Prestado     |
+---------------------+
```

### Elementos de los diagramas de Casos de Uso

<img src=images/elementos-diagramas-de-casos-de-uso.png width="400">

#### Ejemplos

<img src=images/diagrama-caso-uso.png width="300">

<img src=images/diagrama-caso-uso-1.png width="300">

<img src=images/diagrama-caso-uso-3.png width="300">

> ***Para realizar los digramas de casos de uso utilizaremos [https://app.diagrams.net/](https://app.diagrams.net/)***

> **Ejemplo:** El sistema de gestión de una tienda online permite a dos tipos de usuarios interactuar con las funcionalidades principales del sistema: Usuarios comunes y Administradores. A continuación, se describen los actores y los casos de uso asociados.

<details>
  <summary>AYUDA</summary>

- `Actores`:
  - Usuario: Es el cliente que utiliza la plataforma para buscar productos y realizar pedidos.
  - Administrador: Es la persona encargada de gestionar la tienda, quien controla el inventario y los precios de los productos.
- Casos de Uso:
  - Buscar Producto:El Usuario puede buscar productos en el catálogo de la tienda utilizando el sistema.
  - Realizar Pedido:El Usuario puede seleccionar productos del catálogo y realizar un pedido.
  - Gestionar Inventario:El Administrador puede actualizar la disponibilidad de productos en el inventario (agregar o eliminar productos).
  - Actualizar Precios:El Administrador puede modificar los precios de los productos en el catálogo.

- `Flujo básico`:
  - El Usuario accede al sistema y puede Buscar Productos en el catálogo. Una vez que encuentra los productos deseados, el Usuario puede Realizar un Pedido.
  - El Administrador tiene acceso a las funciones de gestión, donde puede Gestionar el Inventario de productos, agregando o quitando productos, y Actualizar los Precios de los productos existentes.
- Restricciones:
  - Solo el Administrador tiene acceso a las funcionalidades de gestión del inventario y modificación de precios.
  - Los Usuarios no tienen permisos para acceder a la gestión interna del sistema.
</details>

### [Especificación de los Casos de Uso](casos-de-uso/ESPECIFICACION.md)

### [Ejemplo](casos-de-uso/EJEMPLO.md).

## 2. Diagrama de Secuencia

### Campo de Aplicación

- Se utiliza para modelar cómo los objetos interactúan en un flujo temporal a lo largo de un escenario específico.
- Ideal para representar la __lógica__ de un proceso o una funcionalidad dentro del sistema.

### Componentes

- **Línea de Vida de un Objeto**:
  - Representa la existencia de un objeto en el tiempo.
  - Se visualiza como una línea vertical que se extiende hacia abajo.

- **Activación**:
  - Representa el período durante el cual un objeto está activo (ejecutando una acción).
  - Se representa como un rectángulo vertical sobre la línea de vida.

- **Envío de Mensajes**:
  
  - Indica la comunicación entre objetos mediante flechas.
  - Se puede especificar el tipo de mensaje (síncrono, asíncrono).

### Ejemplo

```texplain
Cliente         Sistema         Base de Datos
   |                |                 |
   | Solicitar página web             |
   |-------------->|                  |
   |                |                 |
   |      Consultar datos             |
   |---------------------->|          |
   |                |                 |
   |      Respuesta con datos         |
   |<----------------------|          |
   |                |                 |
   |  Generar respuesta               |
   |<--------------|                  |
   |                |                 |
   | Mostrar página                   |
   |<---------------------------------|
```

#### Explicación

- Cliente solicita una página web al Sistema.
- Sistema realiza una consulta a la Base de Datos.
- La Base de Datos responde con los datos solicitados.
- El Sistema genera una respuesta y la envía de vuelta al Cliente.
- El Cliente recibe y muestra la página web.

<details>
  <summary>EJEMPLO REAL</summary>

  ### Diagrama de Secuencia: Proceso de Compra en Línea

  Este diagrama de secuencia representa el flujo de interacciones entre un usuario, un sistema de compras en línea, un carrito de compras y una base de datos durante el proceso de compra en línea.

  El diagrama sigue los siguientes pasos:

  1. **Inicio de Sesión:**
    - El usuario inicia sesión en el sistema.
    - El sistema verifica las credenciales del usuario.

  2. **Ver Carrito de Compras:**
    - El sistema muestra al usuario los productos que tiene en su carrito de compras.

  3. **Agregar Producto al Carrito:**
    - El usuario agrega un producto al carrito de compras.

  4. **Realizar Pago:**
    - El usuario decide realizar el pago.
    - El sistema procesa el pago, verificando la disponibilidad de los productos en la base de datos.
    - La base de datos confirma la disponibilidad de los productos y el sistema descuenta los productos del inventario.
    - El sistema actualiza el inventario en la base de datos.

  5. **Confirmación de Pago:**
    - El sistema confirma al usuario que el pago se ha realizado correctamente.

  6. **Verificar Estado del Pedido:**
    - El usuario verifica el estado de su pedido.
    - El sistema consulta el estado del pedido en la base de datos.
    - La base de datos devuelve el estado del pedido al sistema.
    - El sistema muestra al usuario el estado de su pedido.

  ![Diagrama de Secuencia](images/diagrama-secuencia.png)

</details>

## 3. Diagrama de Colaboración

### Campo de Aplicación

- Se utiliza para mostrar cómo los objetos colaboran en un escenario específico, enfatizando las relaciones entre ellos.
- Ideal para ilustrar la interacción en un contexto más amplio que el proporcionado por un diagrama de secuencia.

### Componentes

- **Objetos**:
  - Representan instancias de clases que participan en la interacción.
  - Se representan como rectángulos etiquetados.

- **Mensajes**:
  - Indican la comunicación entre objetos.
  - Se etiquetan con el nombre del mensaje y el número de secuencia (opcional) para indicar el orden de la interacción.

### Ejemplo
```plaintext
Objeto1              Objeto2               Objeto3
   |                    |                     |
   |--(1) Solicitar --->|                     |
   |                    |                     |
   |                    |--(2) Consultar ---> |
   |                    |                     |
   |                    |<-(3) Respuesta ---- |
   |<-(4) Respuesta ----|                     |
   |                    |                     |
```

#### Explicación

- `Objeto1` solicita una acción a Objeto2.
- `Objeto2` realiza una consulta a Objeto3.
- `Objeto3` responde a Objeto2.
- `Objeto2` finalmente responde a Objeto1.

## Licencia 📄

Este proyecto está bajo la Licencia (Apache 2.0) - mira el archivo [LICENSE.md](../../LICENSE.md) para detalles
