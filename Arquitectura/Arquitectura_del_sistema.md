# Arquitectura del sistema — ZetaVision (cliente-servidor)

| Componente de sistema | Tecnología o framework | Versión | Puerto | Descripción de uso o requisitos | Enlace a documentación |
|---|---|---|---|---|---|
| Hardware | Servidores VM, procesador CPU 11th Gen Intel(R) Core(TM) i7-11700 @ 2.50GHz, RAM 8GB, disco 50GB, adaptador de red puente y red interna | no | no | Máquina que ejecuta el servidor Ubuntu con la web, la base de datos y Coolify. Como mínimo, recursos suficientes para ejecutar los servicios a la vez y una tarjeta de red gigabit. | no |
| Sistema operativo | Ubuntu Server para los servicios web; Windows Server (propietario) para el dominio (AD DS, DNS, DHCP); Windows 11 como cliente | Ubuntu Server 24.04 LTS ; Windows Server 2022; Windows 11 | no | Ubuntu aloja la web y la base de datos en la DMZ. Windows Server gestiona usuarios, nombres y direcciones de la red interna. Windows 11 es el puesto cliente del dominio. | https://ubuntu.com/server/docs |
| Interfaz de usuario (Frontend) | HTML5, CSS3 y JavaScript sin framework, con three.js y Lenis | three.js 0.160.0; Lenis 1.1.20 | 443 (HTTPS, servido por el servidor web) | Web de presentación con las gafas en 3D, animación por scroll, vídeo de introducción, documentación, tienda y acceso. Se ejecuta en el navegador del cliente. | https://threejs.org/docs/ |
| Lógica de negocio (Backend) | Node.js con Express | Node.js 22 LTS; Express 5.x | 3000 (interno, detrás del servidor web) | Login real, tienda y pedidos. Hoy la web es solo frontend, por lo que esta parte está pendiente de implementar. | https://expressjs.com/ |
| Servidor web | Nginx , publicado para el dominio zetavision.com | 1.24 (versión de Ubuntu 24.04) | 80 (redirige) y 443 (HTTPS) | Sirve el HTML, el CSS y el JavaScript, y actúa como proxy hacia el backend. El certificado HTTPS se gestiona para el dominio zetavision.com. | https://nginx.org/en/docs/ |
| Base de datos | MySQL  | 8.0 | 3306 (acceso protegido) | Guarda usuarios, pedidos y datos de la tienda. Solo debe ser accesible desde el backend. | https://dev.mysql.com/doc/ |
| Sistema gestor de base de datos | phpMyAdmin | 5.2 | 443 (a través del servidor web, con acceso restringido) | Interfaz para crear tablas, usuarios y consultas de la base de datos. | https://www.phpmyadmin.net/docs/ |
| Servicios de APIs | REST con JSON sobre HTTPS | no | 443 | El frontend se comunica con el backend mediante peticiones REST (por ejemplo, login y pedidos). Además, Coolify (panel en el puerto 8000, versión 4) gestiona el despliegue de las aplicaciones. | https://coolify.io/docs |

# Diagrama de la red
<img src=../imagenes/Diagrama_de_red.png>
