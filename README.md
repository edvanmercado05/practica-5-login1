# practica-5-login1

# Creación de la carpeta del proyecto
Abrir Visual Studio Code y abrir la carpeta del proyecto.
Instalar y activar el ambiente virtual.
Instalar los siguientes paquetes: Flask, Flask-Login, Flask-MySQLdb y Flask-WTF.
# Estructura de directorio
Estructura de directorio
database
src
models
entities
static
css
img
templates
auth
env
# Archivos de aplicación
# config.py

class DevelopmentConfig():
    DEBUG = True

config = {"development": DevelopmentConfig}
# app.py

from flask import Flask
from config import config

app = Flask(__name__)

@app.route("/")
def index():
    return "<h1>Login</h1>"

if __name__ == '__main__':
    app.config.from_object(config['development'])
    app.run()
# Creación de página HTML principal (HERENCIA)
# Crear un archivo base.html en la carpeta templates con el siguiente contenido:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    {% block miCSS %}{% endblock %}
    <title>{% block titulo %}{% endblock %}</title>
</head>
<body>
    {% block cuerpo %} {% endblock %}
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>

# Herencia de plantillas con Jinja2
Se define en base.html los bloques para título, cuerpo y estilo CSS común.
En las páginas hijas, se extiende de base.html y se define lo específico para cada página.

# Creación de página de login
Crear un archivo login.html en la carpeta auth de templates con herencia a base.html.
En el bloque título se define "Login" y en el cuerpo se coloca el formulario de login.
Creación de ruta para login.html
En app.py, se agrega la ruta /login que renderiza la plantilla login.html.

# Uso de formularios
Se agrega un formulario para usuario y contraseña en login.html.
Se agrega un archivo login.css en static/css y se referencia en login.html para estilos adicionales.

# Esquema de ruteo de login
Se crea una página home.html en templates que herede de base.html y muestre un mensaje de bienvenida.
Se modifica app.py para que la ruta raíz redirija a la ruta /login.
Se modifica la ruta /login para aceptar métodos GET y POST.
Si se recibe un POST con usuario "admin" y contraseña "123", se redirige a la página home, de lo contrario se vuelve a mostrar la página de login.
Si se accede mediante GET, se renderiza la plantilla de login.
Este es un resumen de los pasos necesarios para crear una aplicación de login con Flask. Puedes seguir estos pasos y adaptarlos según tus necesidades y requisitos específicos.
