# Informe del Examen

## Introducción

Este documento describe los pasos que he seguido para completar el examen, las herramientas que he utilizado y las pruebas que demuestran que cada uno de los objetivos se ha cumplido.

---

## Pasos Seguidos

### Paso 1: Configuración del Entorno

1. **Acceso al VPS:**
   ```sh
   ssh root@MI-IP
   ```
2. **Actualización de paquetes:**
   ```sh
   sudo apt update
   ```
3. **Clonación del repositorio:**
   ```sh
   git clone <URL-DEL-REPO>
   cd NOMBRE-REPO
   ```
4. **Instalación de dependencias:**
   ```sh
   sudo apt install npm
   npm install -g pm2
   npm install
   ```

---

### Paso 2: Ejecución del Script de Despliegue

Ejecuté el script `deploy.sh`, que realiza las siguientes acciones:

- **Actualiza los paquetes del sistema.**
- **Instala las dependencias necesarias:**
  ```sh
  sudo apt install npm nodejs certbot
  ```
- **Genera certificados SSL con certbot.**
- **Copia los certificados a la ubicación esperada por la aplicación:**
  ```sh
  cp /etc/letsencrypt/live/dev3.cyberbunny.online/fullchain.pem /ruta/destino
  cp /etc/letsencrypt/live/dev3.cyberbunny.online/privkey.pem /ruta/destino
  ```

---

### Paso 3: Inicio del Servidor

Ejecuté el servidor con HTTPS configurado:

```sh
node server.js
```

Para verificar su estado, revisé los logs y confirmé que estaba funcionando correctamente.

---

### Paso 4: Configuración de GitHub Actions

Configuré los secretos en GitHub para la automatización del despliegue:

- **SSH_HOST:** Dirección IP o nombre de host del servidor.
- **SSH_USER:** Nombre de usuario SSH.
- **SSH_PASSWORD:** Contraseña del usuario SSH.

También actualicé el archivo `deploy.yml` para manejar el despliegue automático en la rama `main`. Es decir pm2 stop mi-aplicacion(nombre que le has puesto en pm2 a la hora de inicarlo con pm2 start server.js --name test-deploy) && cd ExamenDiegoFinal(repo en el que estoy trabajando) && git pull && npm install && pm2 start mi-aplicacion &



---

### Paso 5: Pruebas

1. **Verificación de HTTPS:**
   - Accedí a [https://dev3.cyberbunny.online](https://dev3.cyberbunny.online) y confirmé que el sitio web se carga correctamente con HTTPS.

2. **Pruebas de CORS:**
   - Realicé solicitudes desde un origen diferente y verifiqué que las respuestas se recibían correctamente, confirmando que CORS estaba configurado adecuadamente.

---

## Herramientas Utilizadas

- **VPS:** Linode, para alojar la aplicación.
- **GitHub Actions:** Para automatizar el despliegue (CI/CD).
- **Certbot:** Para generar certificados SSL.
- **PM2:** Para gestionar el proceso del servidor y despliegue.

---

### Evidencias

#### Capturas de pantalla

![Configuración del despliegue](image-1.png)

![Pruebas de CORS y HTTPS](image.png)

