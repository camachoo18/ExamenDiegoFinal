Paso 1: Una vez tenga creado mi proyecto, tengo que acceder a mi vps

Paso 2: Instalar las dependencias necesarias
npm i

Paso 3: Configurar el servidor (server.js)
lo que tengo en mi server.js

Paso 5: Ejecuto el script de despliegue en mi vps 
Ejecuta el script de despliegue para instalar las dependencias y generar los certificados SSL.

./deploy.sh

Paso 6: Inicio el servidor
Inicio el servidor con HTTPS configurado.
node server.js

Con estos pasos, mi proyecto esta configurado para usar HTTPS y CORS.



## Una vez se tenga el dominio cyberbunny con https y cors, toca hacer un deploy cd/ci
# Importante una vez tenga mi proyecto funcionando en el dominio de cyberbunny con https y cors, deberia acceder a la terminal y subir por ssh mi vps ANTES QUE NADA:
ssh root@MI-ip
sudo apt update
git clone https://github.com/camachoo18/NOMBRE-REPO.git
sudo apt install npm
npm install -g pm2
cd mi-repo
npm install

pm2 start server.js --name "mi-aplicacion"
pm2 stop mi-aplicacion
pm2 delete mi aplicacion

pm2 save
pm2 startup

# Paso 1: Configurar los secretos en GitHub
Ve a tu repositorio en GitHub.
Haz clic en "Settings" (Configuración).
En el menú de la izquierda, selecciona "Secrets and variables" y luego "Actions".
Haz clic en "New repository secret" y añade los siguientes secretos:
SSH_HOST: La dirección IP o el nombre de host de tu servidor.
SSH_USER: El nombre de usuario para conectarse a tu servidor.
SSH_PASSWORD: La contraseña para el usuario SSH.

# Paso 2: Actualizar el archivo deploy.yml (ya lo he aplicado antes con el https)
Asegúrate de que tu archivo deploy.yml esté configurado correctamente para realizar el despliegue.

# Paso 5: Hacer un push a la rama main
Haz un commit y un push de tus cambios a la rama main de tu repositorio en GitHub.
git add .
git commit -m "Configurar HTTPS y CORS para despliegue"
git push origin main

# Paso 6: Verificar el despliegue
Una vez que hagas push a la rama main, GitHub Actions debería ejecutar el flujo de trabajo definido en deploy.yml y desplegar tu aplicación en el servidor remoto. Puedes verificar el estado del despliegue en la pestaña "Actions" de tu repositorio en GitHub.

 debería estar desplegada y funcionando en tu VPS con HTTPS y CORS configurados. PM2 se encargará de gestionar tu aplicación


# Importante
SSH_HOST--ES MI IP de linode
SSH_USER--es root
SSH_PASSWORD--ES la contrasena que nos da diego
