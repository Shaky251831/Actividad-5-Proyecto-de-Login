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
