🧩 PokeDex - Despliegue en la Nube con Azure Static Web Apps
📌 Descripción del Proyecto

Este proyecto consistió en el despliegue de una aplicación web llamada PokeDex, desarrollada en Angular, la cual permite explorar diferentes especies de Pokémon mostrando información detallada obtenida desde la API pública de Pokémon.

Durante la actividad se implementó el despliegue en la nube utilizando Azure Static Web Apps, integrando automatización CI/CD con GitHub Actions y aplicando configuraciones de seguridad web mediante encabezados HTTP.

☁️ Configuración del Entorno en Azure

Para realizar el despliegue se utilizó una cuenta personal de Azure con la prueba gratuita disponible para nuevos usuarios, lo que permitió acceder a los servicios cloud necesarios para publicar la aplicación.

Pasos realizados:
Creación de una cuenta personal en Azure.
Activación de la prueba gratuita de Azure.
Configuración inicial de la suscripción y recursos.
Creación del recurso Static Web Apps en Azure.
Vinculación del repositorio de GitHub con Azure para automatizar el despliegue.

🚀 Integración Continua y Despliegue Automático

Se creó automáticamente un workflow de GitHub Actions para automatizar el proceso de compilación y despliegue de la aplicación.

Commit realizado:
ci: add Azure Static Web Apps workflow file

Este commit agregó el archivo:

.github/workflows/azure-static-web-apps-polite-rock-0a8ed1410.yml
Funcionalidades implementadas:
Ejecución automática en cada push a la rama master.
Compilación automática del proyecto Angular.
Despliegue automático en Azure Static Web Apps.
Integración con Pull Requests.
Uso seguro de secretos mediante tokens de Azure y GitHub.
Configuración importante:
app_location: "/sistemas-distribuidos/poke-dex-lab/source/pokedex-angular"
output_location: "dist/pokedex-angular"

Estas rutas permitieron indicarle a Azure:

dónde se encuentra el código fuente Angular,
y dónde se genera la carpeta de producción después del build.
🔧 Corrección de Rutas en Producción
Commit realizado:
Update imagesPath in production environment

Se modificó el archivo:

environment.prod.ts
Cambio realizado:
imagesPath: '/pokedex-angular/assets/images',

por:

imagesPath: '/assets/images',
Objetivo del cambio:

Corregir la carga de imágenes en producción dentro de Azure Static Web Apps.

Problema encontrado:

La aplicación estaba intentando acceder a imágenes usando una ruta incorrecta, lo que ocasionaba que algunos recursos estáticos no cargaran correctamente después del despliegue.

Solución aplicada:

Se ajustó la ruta base de las imágenes para que funcionara correctamente desde el entorno de producción generado por Angular y servido por Azure.

🔒 Implementación de Seguridad Web
Commit realizado:
Create staticwebapp.config.json for app settings

Se creó el archivo:

staticwebapp.config.json
Funcionalidades implementadas:
🔁 Navegación SPA
"navigationFallback": {
  "rewrite": "/index.html"
}

Esto permite que Angular maneje correctamente las rutas internas evitando errores 404 al refrescar páginas.

🛡️ Encabezados HTTP de Seguridad

Se configuraron múltiples encabezados de seguridad:

Content-Security-Policy
Strict-Transport-Security
X-Content-Type-Options
X-Frame-Options
X-XSS-Protection
Referrer-Policy
Permissions-Policy
Beneficios obtenidos:
Prevención de ataques XSS.
Protección contra clickjacking.
Bloqueo de carga insegura de contenido.
Restricción de permisos innecesarios del navegador.
Mejora significativa de la seguridad del sitio.

Gracias a esta configuración, la aplicación obtuvo una mejor calificación en herramientas de análisis de seguridad web.

🌐 Resultado Final

La aplicación fue desplegada exitosamente en Azure y quedó disponible mediante una URL pública generada automáticamente por Azure Static Web Apps.

El sistema quedó con:

despliegue automático,
integración continua,
manejo correcto de rutas Angular,
carga correcta de recursos estáticos,
y configuraciones avanzadas de seguridad web.
🧠 Reflexión Técnica

Durante el desarrollo y despliegue del proyecto se reforzaron conocimientos relacionados con:

DevOps básico,
integración continua (CI/CD),
despliegue cloud,
configuración de workflows,
manejo de entornos Angular,
y seguridad web.

Uno de los principales desafíos fue configurar correctamente las rutas del proyecto Angular dentro de Azure y ajustar los recursos estáticos para producción.

📌 Conclusión

El proyecto permitió aplicar conceptos modernos de despliegue web utilizando Azure Static Web Apps y GitHub Actions, automatizando completamente el proceso de publicación de la aplicación.

Además, se implementaron buenas prácticas de seguridad y configuración SPA, logrando una aplicación funcional, segura y accesible desde la nube.
