# Instalación Plataforma de telesalud Todo en una v1.0 basada en OpemEMR  v7.0.0 

Seguir los pasos de instalación del siguiente enlace. https://github.com/ciips-code/openemr-telesalud/blob/release/v1.0/Documentation/INSTALL

Se puede descargar la versión 1.0 de siguiente manera:
```
git clone https://github.com/ciips-code/openemr-telesalud openemr-telesalud
git checkout release/v1.0
```

## Post instalacion 
Una vez instalado OpenEmr y configurado la Base de datos debe ejecutar los siguientes archivos via sql dump
1. Listas y traducciones: /telehealth/sql/ops-openemr-data-upgrade.sql
1. Configuración Documentos: /telehealth/sql/documentos-teleconsulta.sql
1. Actualizaciones tablas: /telehealth/sql/ops-openemr-upgrade.sql


## Actualización al CIE-11
```
cd path/to/project/telehealth/util
```
Abrir el archivo load_icd_es.php y editar los siguientes valores:
```
$host           = 'localhost';
$port           = '3306';
$username       = 'openemr_db_username';
$password       = 'openemr_db_password';
$db             = 'openemr_db_database';
```

Una vez establecido lo valores correr el script:
```
php load_icd_es.php
```


## Configurar sistema
Luego acceder al sistema via web server e ir al menu Administración / Formularios / Formularios de administración y dejar las configuraciones  como se describen a continuacion: 
- Desactivar todos los formularios de la vista/encuentro que no sean los siguientes:
    - [ ] Plan de atención	    (inhabilitado)	
    - [ ] Clinical Instructions	(inhabilitado)
    - [X] Nota Clínica	        (activado) 
    - [ ] Eye Exam	            (inhabilitado) 
    - [ ] Hoja de tarifas	    (inhabilitado) 
    - [ ] Functional and Cognitive Status	(inhabilitado) 
    - [ ] Group Attendance Form	(inhabilitado) 
    - [ ] Diversas opciones de facturación HCFA	(inhabilitado) 
    - [ ] Formulario Nueva Visita	(inhabilitado) 
    - [X] New Group Encounter Form	(activado) 
    - [ ] Observation	            (inhabilitado) 
    - [ ] Orden de Procedimiento	(inhabilitado) 
    - [ ] Revisión de los sistemas	(inhabilitado) 
    - [ ] Revisión de chequeos de sistemas	(inhabilitado) 
    - [X] SOEP	                    (activado) 
    - [ ] Dictado	                (inhabilitado) 
    - [X] Signos Vitales	        (activado)

## Variables de entornos archivo .env
Estas variables deben configurarse para que el módulo de teleconsulta funcione correctamente. El archivo debe estar en el direcotrio principal de la aplicacion OpenEMR

################################
## CONFIGURACION API SERVIDOR DE VIDEO CONSULTAS
################################

### URL Servidor
VC_API_URL='https://meet.telesalud.iecs.org.ar'
### Endpoint 
VC_API='/api/videoconsultation?'
### Endpoint de datos
VC_API_DATA='/api/videoconsultation/data?'
### Puerto
VC_API_PORT=NRO DE PUERTO
### Token access
VC_API_TOKEN=TOKEN DE ACCESO

################################
## CONFIGURACION SERVIDOR DE BASE DE DATOS
################################

## DATA BASE CONNECTIONS SETTING
OPS_DB_HOST=HOST DE BASE DE DATOS 
OPS_DB_PASSWORD=CONTRASEÑA DE BASE DE DATOS
OPS_DB_USER=USUARIO DE BASE DE DATOS
OPS_DB_DATABASE=NOMBRE DE BASE DE DATOS