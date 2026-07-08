# Actividad 5. Proyecto de Login

## Portada
- Docente: Martínez Nieto Adelina.

- Curso: Programación Web 2026.

## Nombre del Proyecto
 Control Escolar.

## Integrantes del Equipo:

- Márquez Agustín Briseida.
- Lopez Guerrero Ariel Betsabe.


## Descripción

Aplicación web que simula un entorno de control escolar. Cuenta con un módulo de inicio de sesión (Login) seguro que valida las credenciales del usuario y un panel de administración principal (Dashboard):

- Barra de navegación superior.
- Menú lateral (Sidebar) responsivo.
- Secciones dinámicas para la captura de datos (Alumnos y Usuarios).
- Cálculo automático de edad.

## Explicación y documentación: 

### Framework CSS Utilizado

Se utilizó **Bootstrap 5**, un framework basado en componentes que permite un diseño limpio, moderno y completamente responsivo mediante clases utilitarias predefinidas (como `d-flex`, `card`, `shadow-lg`,Esto facilitó estructurar del Login como la distribución en paralelo del Sidebar y las secciones del panel.

### Flujo del Login hacia el Sistema

1. El usuario ingresa a `login.html`.
2. Introduce su correo electrónico y contraseña. Al presionar "Ingresar", el evento `submit` es interceptado por JavaScript.
3. Se ejecutan las funciones de validación de la librería `utileria.js`.
4. Si las credenciales coinciden con las registradas, el script guarda los datos necesarios en el navegador y redirige automáticamente al panel principal (`index.html`) mediante `window.location.href`.

### Transferencia del Nombre de Usuario del Login al Navbar

Para pasar datos entre páginas distintas sin usar una base de datos en el servidor, se empleó la API de `localStorage`:

**En `login.html`:** Tras validar con éxito el correo, se extrae el nombre de usuario y se almacena en el navegador con la instrucción:

```javascript
localStorage.setItem('usuarioLogueado', nombreDelUsuario);
```

**En `index.html`:** En cuanto la página carga, un script lee ese espacio de memoria con:

```javascript
const usuario = localStorage.getItem('usuarioLogueado');
```

Inmediatamente después, inserta ese texto directo en la etiqueta correspondiente del Navbar usando `.innerText`, personalizando la interfaz en tiempo real.

### Métodos Principales (Librería `utileria.js`)

El proyecto integra una librería personalizada de JavaScript orientada a la manipulación y validación de datos:

| Método | Descripción |
|---|---|
| `soloLetras(texto)` | Expresión regular que restringe la entrada de datos para asegurar que campos como el "Nombre" no contengan números ni caracteres especiales. |
| `validarLongitud(campo, min, max)` | Verifica que la extensión de un texto (como el número de control) cumpla con los límites mínimos y máximos requeridos. |
| `calcularEdad(fechaNacimiento)` | Toma la fecha ingresada en el formulario, la compara con el año actual (2026) y devuelve de forma exacta la edad del alumno. |

## Proceso de Creación:

### Paso 1: Maquetación del Login y Navbar Superior.

Se diseñó una interfaz limpia centrada en pantalla con un contenedor `vh-100` y una tarjeta flotante (`card`) con sombras pronunciadas. El formulario incluye cajas de texto validadas por Bootstrap y un botón principal azul de tipo `submit`. En el archivo principal, se añadió una barra superior  (`bg-dark`) que alberga el título del sistema, el nombre dinámico rescatado de `localStorage` y un botón estilizado para Salir/Cerrar Sesión.

### Paso 2: El Sidebar Lateral Responsivo.

Se distribuyó el cuerpo de `index.html` usando un contenedor flexible (`d-flex`). A la izquierda se reservó una columna fija de navegación (`#sidebar`) donde se organizaron botones de acceso para alternar entre los submódulos de "Captura de Alumnos" y "Gestión de Usuarios".

### Paso 3: Número de Control y Secciones Dinámicas.

Dentro del panel central, se programó el formulario de registro de estudiantes. Este incluye el campo para el "Número de Control" con restricciones de longitud fija, además de campos para capturar el nombre y el teléfono.

### Paso 4: El Modal de Alerta Personalizado.

En lugar de usar los `alert()` nativos del navegador, se maquetó un componente flotante oculto por defecto con CSS (`display: none;` y `position: fixed;`). Cuando el formulario de alumnos se procesa con éxito, el script calcula la edad del estudiante y altera las clases del modal pasándole la propiedad `display: flex;` para mostrar una ventana emergente estilizada que confirma el registro exitoso.

## Capturas de Pantalla.
<img width="589" height="312" alt="Imagen1" src="https://github.com/user-attachments/assets/1b5b55b7-699f-4882-b941-df1f345bd1f8" />
<img width="589" height="309" alt="Imagen2" src="https://github.com/user-attachments/assets/ceb659ae-b2ce-4996-9138-c31b84e1a559" />
<img width="589" height="310" alt="Imagen3" src="https://github.com/user-attachments/assets/4f89b358-b3a2-4c7e-8290-edefbc16f2a7" />
<img width="589" height="308" alt="Imagen4" src="https://github.com/user-attachments/assets/8b5cd7d0-d338-4c9f-bdca-d5b6988ed494" />
<img width="589" height="313" alt="Imagen5" src="https://github.com/user-attachments/assets/cac0650d-064a-4923-b5d9-cd2f45493fb6" />

