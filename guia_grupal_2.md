# Guia para mostrar un template con Django

Para mostrar un template en Django, primero es necesario tener una comprensión básica de la estructura de un proyecto Django y la relación entre sus componentes principales: proyectos, aplicaciones, vistas y templates. A continuación, te guiaremos a través de un proceso paso a paso para mostrar un template simple en Django.

## Crear un proyecto y una aplicación Django

1. Instala Django, si aún no lo has hecho:
- pip install django

2. Crea un nuevo proyecto Django:
- django-admin startproject myproject

3. Cambia al directorio del proyecto:
- cd myproject

4. Crea una nueva aplicación Django:
- python manage.py startapp myapp

## Crear un template

1. En la carpeta de tu aplicación (myapp), crea un directorio llamado "templates".
2. Dentro del directorio "templates", crea un archivo llamado "index.html".
3. Agrega el siguiente contenido básico de HTML en "index.html":

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mi primer template Django</title>
</head>
<body>
    <h1>Bienvenido a mi primer template Django</h1>
</body>
</html>
```

## Configurar la vista

1. En "myapp/views.py", importa el módulo "render" e implementa una función llamada "index" que renderice el template:

```
from django.shortcuts import render

def index(request):
    return render(request, 'index.html')
```

## Configurar la URL

1. En "myapp", crea un archivo llamado "urls.py".
2. En "myapp/urls.py", importa la vista "index" y define la URL:

```
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

3. En "myproject/urls.py", importa "include" y enlaza la URL de la aplicación:

```
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
]
```

## Ejecutar el servidor de desarrollo

1. Ejecuta el siguiente comando para iniciar el servidor de desarrollo:
- python manage.py runserver

2. Abre tu navegador web y ve a http://127.0.0.1:8000/. Deberías ver tu template renderizado con el mensaje "Bienvenido a mi primer template Django".

