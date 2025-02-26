---
title: Introduccion a entornos virtuales en Python
published: true
---

# Entornos virtuales en python 3

Es de buena practica aislar nuestros proyectos en python para evitar 
conflictos con dependencias de paquetes (a.k.a bibliotecas, no librerias)
Para ello, python dispone de diversos modulos(pip), por citar:

* pipenv
* virtualenv
* venv 
* pipx 

Personalmente encuentro muy comodo usar pipenv y venv, en este caso usaremos venv.
Este documento asume que python y pip está instalado en tu computadora.

Creamos un directorio de trabajo para nuestro proyecto, en sistemas tipo Unix, 
se haría de la siguiente manera.

### Creando el directorio de trabajo.

```
  $ mkdir proyecto1
  $ cd proyecto1
  ~/proyecto1 $
```

### Creando el entorno.

Siguiente paso es crear el entorno virtual para ejecutar modulos de python
que usará nuestro proyecto, por citar: (pandas, jupyter, notebook, numpy, etc.)
en nuestro caso usamos el modulo venv y el directorio para almacenar los modulos
aislados se llamará .venv

 ```
~/proyecto1 $ python3 -m venv .venv
 ```

### Activando el enterno.

```
  ~/proyecto1 $ source .venv/bin/activate
```

### Instalando modulos

```
  ~/proyecto1 $ python -m pip install jupyter notebook pandas numpy seaborn matplotlib 
```

En este punto, tenemos instalado nuestro entorno virtual de python con los modulos
necesarios para comenzar nuesto proyecto.

### Desactivando el entorno.

Es de buena practica, salir del entorno cuando terminos de trabajar o necesitemos cambiar 
de proyecto, se hace de la siguiente manera.

```
 ~/proyecto1 $ deactivate 
```



