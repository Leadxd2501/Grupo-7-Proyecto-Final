# Grupo-7-Proyecto-Final
Informe de la instalación de una distribución y LAMP, grupo 7 de la materia de Sistemas Operativos 2, Turno Medio día, diciembre 2023.
## Introducción
En este documenta estaremos viendo como se instala una distribución de Linux (que en este caso la distribución a instalar será “CentOS”) y está la estaremos ejecutando en “Oracle VM VirtualBox” al igual que se mostrará con imágenes, códigos y descripciones de los mismo de manera clara y entendible a parte también se estará instalando en la misma distribución"LAMP" y “WordPress”. 
## Marco Teorico
Antes de ver lo que vamos a instalar primero tenemos que ver algunos conceptos claves.
### CentOS
Abreviatura de Community ENTerprise Operating System, es una distribución de Linux basada en el código fuente de Red Hat Enterprise Linux (RHEL). Fue creada con el objetivo de proporcionar un sistema operativo de clase empresarial de código abierto, estable y de alto rendimiento. 
CentOS fue lanzado por primera vez en 2004. Es desarrollado por un grupo de voluntarios que toman los paquetes fuente de RHEL, los recompilan para eliminar las marcas registradas y logotipos de Red Hat, pero manteniendo la compatibilidad binaria.
### MySQL
Es un sistema de gestión de bases de datos relacional de código abierto ampliamente utilizado en aplicaciones web y empresariales.
Fue creado por suecos Michael Widenius y David Axmark junto con finlandés Monty Widenius, lanzado por primera vez en 1995. Desde entonces, ha experimentado múltiples versiones y adquisiciones, siendo una de las bases de datos más populares en el mundo. 
### Apache 
Apache es un servidor web de código abierto muy popular y potente. 
Apache HTTP Server, comúnmente conocido como Apache, fue desarrollado por la Apache Software Foundation. Su desarrollo comenzó en 1995 y desde entonces ha sido uno de los servidores web más utilizados en el mundo. 
### PHP
PHP es un lenguaje de programación utilizado principalmente para crear sitios web dinámicos. 
Fue creado en 1994 por Rasmus Lerdorf y se destaca por su integración sencilla con HTML. PHP permite a los desarrolladores crear páginas web interactivas y dinámicas al ejecutar código en el servidor.
## Desarrollo
Ahora estaremos viendo como es que se descargo la distribución y se lo ejecuto en Oracle VM VirtualBox:
Primero se descarga el CentOs 7, lo colocamos en VirtualBoz y seguimos las indicaciones que nos pide:
![Imagen de WhatsApp 2023-12-20 a las 12 33 23_eb00cbb1](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/04caf6f8-9191-41b1-a962-8caf5178138d)

Seguido de esto colocamos el siguiente comando para iniciar la **instalación de Apache**: 
```
sudo yum install httpd
```
Despues de eso **habilitamos las consultas wed** con los siguientes comandos:
```
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload
```
![12](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/d35f90cb-1575-41b0-8b5e-61c084daf3e5)

Seguido de esto **habilitamos y activamos Apache** 
Habilitamos el servicio para lograr que el servidor se active automáticamente al reiniciar el sistema operativo con el siguiente codigo:
```
sudo systemctl enable httpd.service
```
Activar servicio con el siguiente comando:
```
sudo systemctl start httpd.service
```
Iniciamos el servidor con el siguiente comando:
```
sudo systemctl start httpd
```
Despues **verificamos el estado de Apache**
Si todo ha salido bien, mostrará el siguiente resultado:

![123](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/ac7d60d6-2840-4f64-a887-9ad7eab9c027)

tambien podemos verficar con el navegador wed colocando http://ip-servidor/, para saber la ip del servidor colocamos en la terminal **nmcli** y donde diga **inet4** ese es nuestra ip:

![Imagen de WhatsApp 2023-12-20 a las 17 14 36_418ed216](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/562ed062-565a-43c7-abbd-1a749a9fcece)

A continuación vamos a descargar el **servidor MySQL**
**Instalar MySQL**
Con el siguiente comando:
```
sudo yum install mariadb-server mariadb
```
![Imagen de WhatsApp 2023-12-20 a las 17 16 29_6d047246](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/214e3c05-ec1d-4f15-bedc-deb8bd936a17)

Habilitamos y iniciamos MySQL 
Habilitar el servicio logrará que el servidor se active automáticamente al reiniciar el sistema operativo:
```
sudo systemctl enable mariadb.service
```
Iniciamos el servidor:
```
sudo systemctl start mariadb
```
![Imagen de WhatsApp 2023-12-20 a las 17 19 21_034a3ebc](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/640f6923-9a35-4856-962c-5efc70dc08c2)

Verificamos el estado de MySQL
```
sudo systemctl status mariadb
```
Si todo ha salido bien, mostrará el siguiente resultado:

![Imagen de WhatsApp 2023-12-20 a las 17 22 17_5eadd415](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/dc589621-e398-4e92-94ef-a19dfd94a77e)

Seguido vamos a **instalar el servicio de PHP** 
Instalar PHP
```
sudo yum install php php-mysql
```

![Imagen de WhatsApp 2023-12-20 a las 17 25 26_b8bccf12](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/906d7b25-f297-420e-b28d-e589f5896ef4)

Iniciamos PHP:
```
sudo systemctl restart httpd.service
```
y Verificamos la verción de PHP:
```
php -v
```

![Imagen de WhatsApp 2023-12-20 a las 17 28 37_c2e82a16](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/f2fa77ef-8d18-4a8e-b992-9a2c31d5c6c8)

**Probar PHP + Apache**
Primero instalamo nano si por si acaso no lo tenemos con el siguiente copdigo:
```
sudo yum install nano
```
![Imagen de WhatsApp 2023-12-20 a las 18 04 15_8a9aa82d](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/19a8544a-6311-4774-9118-a18e8a01fa2c)

Con nano instalado podemos editar el archivo info.php el cual no existe previamente el directorio del contenido de Apache  (/var/www/html/) creamos y editamos el archivo con el comando:
```
sudo nano /var/www/html/info.php
```
![Imagen de WhatsApp 2023-12-20 a las 18 04 59_bca99afe](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/b2ac59c8-0897-472a-bb80-00740942d07f)

El contenido de info.php debe ser el siguiente:
```
<?php
phpinfo ();
?>
```
Con el archivo guardado podemos consultar a través del navegador web donde deberemos obtener el siguiente resultado:
http://ip-servidor/info.php

![image](https://github.com/Leadxd2501/Grupo-7-Proyecto-Final/assets/154466596/445f6edf-3710-483e-a6b6-1c3e1a0631ad)

Bueno con todo lo visto ya tenemos instalado correctamente "LAMP" y estaremos listos para la instalación de "WordPress".











