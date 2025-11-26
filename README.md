# Practica 2.1: Instalacion y Configuracion #

## 2. Instalación servidor web Nginx ##
El primer paso consite en actualizar los paquetes del vagrant y despues instalamos NGINX  

```
sudo apt update
sudo apt install nginx
```

Tras eso tenemos que verificar si se ha instalado
```
systemctl status nginx
```
![Imagen status nginx](img/captura-status.png)

## 3. Creación de las carpeta del sitio web ##
A continuacion tenemos que crear las carpetas, y clonar el repositorio:
```
sudo mkdir -p /var/www/antonio.test/html 
cd /var/www/antonio.test/html
git clone https://github.com/cloudacademy/static-website-example
```

Una vez creado y clonado tenemos que dar los permisos: 
```
sudo chown -R www-data:www-data /var/www/antonio.test/html
sudo chmod -R 755 /var/www/antonio.test
```

Y una vez que esta funcionado vemos que funciona 

[https://IP-maq-virtual](https://IP-maq-virtual)

![Imagen IP-maq-virtual](img/captura-funciona.png)

## 4. Configuración de servidor web NGINX ##

Despues tenemos que crear el archivo de configuracion:
```
sudo nano /etc/nginx/sites-available/antonio.test
```
Añadiendo dentro de el: 
```
server {
  listen 80;
  listen [::]:80;
  root /var/www/antonio.test/html; (Esta es nuestra ruta)
  index index.html index.htm index.nginx-debian.html;
  server_name example.test;
  location / {
  try_files $uri $uri/ =404;
  }
}
```

Y creamos un archivo simbolico entre este archivo y el de sitios que estan habilitados:
```
sudo ln -s /etc/nginx/sites-available/example.test /etc/nginx/sites-enabled/
sudo systemctl restart nginx
```

## 4.1. Comprobaciones ##
Ya que no tenemos un servidor DNS vamos a hacerlo de forma manual:
* Editando el archivo hosts de nuestra maquina anfitriona

Para ello tendremos que editar:  /etc/hosts y añadirle:
```
192.168.56.101 antonio.test
```
![Imagen Host](img/antonio.test.png)


Tras todo esto comprobamos que todo se ha registrado correctamente:
![Imagen Registros del servidor](img/comprobacion-registro.png)