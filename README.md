# hotel_reservations_system
Trabajo Final Sistema de Reservas de Hotel COMP3400.SOFTWARE ENGINEERING



Instalación
Paso 1: Preparar las Máquinas Virtuales
Asegúrate de que las VMs estén configuradas correctamente con las siguientes direcciones IP:

VM1: 172.16.5.144
VM2: 172.16.5.145
VM3: 172.16.5.146
Configuración de Red: Las VMs deben estar en la misma red para que puedan comunicarse entre sí. Configura las interfaces de red de las VMs en Red Interna o Adaptador Puenteado.

Comprobación de Conectividad: Desde VM1, prueba hacer ping a VM2 y VM3:

bash
Copy code
ping 172.16.5.145  # Ping a VM2
ping 172.16.5.146  # Ping a VM3
Paso 2: Configurar la Capa de Datos (VM3)
Instalar MariaDB: En VM3, instala MariaDB:

bash
Copy code
sudo apt update
sudo apt install mariadb-server
Configurar la Base de Datos: Crea la base de datos hotel_reservations y un usuario hotel_user con permisos para acceder remotamente:

sql
Copy code
CREATE DATABASE hotel_reservations;
CREATE USER 'hotel_user'@'%' IDENTIFIED BY 'secure_password';
GRANT ALL PRIVILEGES ON hotel_reservations.* TO 'hotel_user'@'%';
FLUSH PRIVILEGES;
Paso 3: Configurar la Capa de Lógica de Negocio (VM2)
Instalar Flask: En VM2, instala Flask y otras dependencias necesarias:

bash
Copy code
pip install flask pymysql
Crear la API en Flask: Crea un archivo app.py con rutas para interactuar con la base de datos y mostrar las reservas.

Paso 4: Configurar la Capa de Presentación (VM1)
Crear la Interfaz de Usuario: En VM1, puedes usar Flask para crear una interfaz de usuario sencilla para ver las reservas.

Conectar a la API en VM2: Asegúrate de que VM1 pueda enviar solicitudes a la API de VM2.

Paso 5: Pruebas
Prueba de Conectividad: Asegúrate de que todas las VMs puedan comunicarse entre sí (ping).

Prueba de la Interfaz de Usuario: Accede a la aplicación Flask desde VM1:

bash
Copy code
http://172.16.5.144:5000
Verificar la Base de Datos: Asegúrate de que las reservas estén siendo almacenadas en MariaDB correctamente.
