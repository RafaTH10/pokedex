# Despliegue — Azure Static Web Apps

## Datos del recurso

| Campo | Valor |
|---|---|
| Servicio | Azure Static Web Apps |
| Proveedor | Microsoft |
| Suscripción | Azure subscription 1 |
| Grupo de recursos | rg-pokedex-prod |
| Nombre del recurso | swa-pokedex-portal-prod |
| Región | Global |
| Plan de hospedaje | Gratis (Free) |

---

## Repositorio GitHub

| Campo | Valor |
|---|---|
| Cuenta GitHub |
| Organización |
| Repositorio | pokedex |
| Rama | master |

---

# Pasos para reproducir el despliegue

## 1. Fork del repositorio base

El proyecto parte del repositorio original `rcuello/ac4dem1a` se realizó un fork generando el repositorio `/pokedex`.

A partir de ese fork se realizaron commits adicionales sobre la rama `master` para agregar la configuración de Azure Static Web Apps y los ajustes necesarios para producción.

## 2. Configuración de Azure Static Web Apps

1. Ingresar al Azure Portal.
2. Crear un recurso → Marketplace → Aplicación web estática.
3. Configurar los datos básicos:

- Suscripción: `Azure subscription 1`
- Grupo de recursos: `rg-pokedex-prod`
- Nombre: `swa-pokedex-portal-prod`
- Plan: `Gratis`

4. En configuración de implementación, seleccionar GitHub como origen y autorizar la cuenta .
5. Seleccionar:
   - Organización: `CuentaGithub`
   - Repositorio: `pokedex`
   - Rama: `master`

6. Configurar las rutas del proyecto Angular:

App location:
/sistemas-distribuidos/poke-dex-lab/source/pokedex-angular

Output location:
dist/pokedex-angular

7. Hacer clic en Revisar y crear → Crear.

Azure genera automáticamente el archivo:

.github/workflows/azure-static-web-apps-polite-rock-0a8ed1410.yml

y ejecuta el primer pipeline CI/CD.

# Commits realizados

## 1. CI/CD Azure Static Web Apps

### Commit:
ci: add Azure Static Web Apps workflow file

Se agregó el workflow de GitHub Actions encargado de:

- Compilar automáticamente el proyecto Angular.
- Ejecutar despliegues automáticos.
- Integrar GitHub con Azure Static Web Apps.
- Desplegar automáticamente en cada push a `master`.

Archivo generado:

.github/workflows/azure-static-web-apps-polite-rock-0a8ed1410.yml

## 2. Corrección de rutas de imágenes

### Commit:
Update imagesPath in production environment

Se modificó el archivo:

src/environments/environment.prod.ts

Cambio realizado:

Antes:

imagesPath: '/pokedex-angular/assets/images',

Después:

imagesPath: '/assets/images',


### Objetivo

Corregir la carga de imágenes en producción dentro de Azure Static Web Apps, ya que algunas rutas no resolvían correctamente después del despliegue.


## 3. Configuración de seguridad y SPA

### Commit:
Create staticwebapp.config.json for app settings

Se creó el archivo:

staticwebapp.config.json


### Configuraciones implementadas

#### Navegación SPA

```json
"navigationFallback": {
  "rewrite": "/index.html"
}


Permite que Angular maneje correctamente las rutas internas evitando errores 404 al refrescar páginas.

#### Encabezados HTTP de seguridad

Se agregaron los siguientes encabezados:

- Content-Security-Policy
- Strict-Transport-Security
- X-Content-Type-Options
- X-Frame-Options
- X-XSS-Protection
- Referrer-Policy
- Permissions-Policy

### Beneficios

- Protección contra ataques XSS.
- Prevención de clickjacking.
- Restricción de contenido inseguro.
- Mejora de seguridad general de la aplicación.

# Ejecución del pipeline CI/CD

El pipeline Azure Static Web Apps CI/CD se ejecutó correctamente en GitHub Actions.

| Job | Estado | Duración |
|---|---|---|
| Build and Deploy Job | ✅ Success | 2m 8s |
| Close Pull Request Job | ⏭️ Skipped | 0s |
| Total | ✅ Success | 2m 20s |


# Resultado del despliegue

| Indicador | Valor |
|---|---|
| Estado | ✅ Success |
| Deployment ID | 4078d9b9-ea05-49be-8d72-e3015a30927f |
| URL del sitio | https://polite-rock-0a8ed1410.7.azurestaticapps.net |

El proyecto permitió desplegar exitosamente una aplicación Angular en Azure Static Web Apps utilizando automatización CI/CD y buenas prácticas de seguridad web.

Además, se logró integrar GitHub Actions para despliegues automáticos y configurar correctamente el entorno de producción, obteniendo una aplicación accesible, funcional y protegida en la nube.
