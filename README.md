# Despliegue de aplicación web: empaquetado, versionamiento y servidor

Proyecto del reto de la unidad 1 de Despliegue de Aplicaciones Web y Móviles.

**Autor:** Jonan Loredo

## Estructura del proyecto

```
Loredo_Jonan_R2_U1/
├── css/
│   └── style.min.css
├── img/
│   └── foto.jpg
├── js/
│   └── main.min.js
├── index.html
└── README.md
```

## Proceso realizado

### 1. Preparación de la aplicación

- Se organizaron los archivos en carpetas: `/css`, `/js` e `/img`.
- **Imagen:** se optimizó con Squoosh (MozJPEG, calidad 75, ancho 1000 px). Peso final: 140 KB.
- **CSS y JS:** se minificaron con cssminifier.com y javascript-minifier.com, generando `style.min.css` y `main.min.js`.
- **Empaquetado:** se generó el archivo `tuapp-v1.0.zip` con la estructura final lista para subir al servidor.

### 2. Versionamiento

- Se creó un repositorio local con `git init` y se subió a GitHub.
- Se hicieron commits descriptivos por cada componente (HTML, CSS, JS e imagen).

### 3. Configuración del servidor (Nginx)

- Se eligió **Nginx 1.30.5** (versión estable para Windows), instalado en `C:\nginx`.
- El paquete `Loredo_Jonan_R2_U1.zip` se extrajo en `C:\nginx\apps\tuapp`, simulando la subida al servidor.
- Se editó `conf/nginx.conf` (copia en `server/nginx.conf`):
  - **Puerto:** `listen 8080;` (se evitó el puerto 80 por posible uso de Apache/XAMPP).
  - **Mapeo de directorios:** el bloque `location /tuapp/` apunta con `alias` a `C:/nginx/apps/tuapp/`.

```nginx
server {
    listen       8080;
    server_name  localhost;

    location /tuapp/ {
        alias C:/nginx/apps/tuapp/;
        index index.html;
    }
}
```

- Comandos usados: `nginx -t` (validar configuración) y `start nginx` (arrancar).
- La aplicación es accesible en **http://localhost:8080/tuapp/**.