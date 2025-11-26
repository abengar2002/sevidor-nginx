# sevidor-nginx

## Practica 2.1: Instalacion y Configuracion ##

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

A continuacion tenemos que crear las carpetas, y clonar el repositorio:
```
sudo mkdir -p /var/www/antonio.test/html 
cd /var/www/example.test/html
git clone https://github.com/cloudacademy/static-website-example
```

Una vez creado y clonado tenemos que dar los permisos: 
```
sudo chown -R www-data:www-data /var/www/antonio.test/html
sudo chmod -R 755 /var/www/antonio.test
```

Y una vez que esta funcionado vemos que funciona 

[https://IP-maq-virtual](https://IP-maq-virtual)

![Imagen IP-maq-virtual](img/captura-status.png)
