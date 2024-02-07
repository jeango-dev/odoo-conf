# VSCode + Docker para el desarrollo en Odoo con completado inteligente

1. Instalar VSCode de su página oficial - <https://code.visualstudio.com>
2. Instalar las extensiones necesarias para el trabajo en Odoo
   - Python Support - <https://marketplace.visualstudio.com/items?itemName=donjayamanne.python-extension-pack>
   - Odoo Support - <https://marketplace.visualstudio.com/items?itemName=trinhanhngoc.vscode-odoo>
   - Odoo Snippets Final (Opcional) - <https://marketplace.visualstudio.com/items?itemName=mjavint.mjavint-odoo-snippets>
3. Crear el espacio de trabajo importando el código fuente de Odoo
4. Configurar y modificar el fichero pyrightconfig.json
5. Compilar la imagen de docker con el fichero Dockerfile
6. Configurar las variables en el .env
7. Configurar el debug en vscode

ARCHIVO .VSCODE: Ubicar en la carpeta raíz del proyecto o del espacio de trabajo

Instalar dependencias del requirements:

1. Copiar Dependencias al Contenedor
   docker cp requirements.txt ${ODOO_CONTAINER_NAME}:/requirements.txt
   Example: docker cp requirements.txt odoo:/requirements.txt
2. Instalar Dependencias
   docker exec -it ${ODOO_CONTAINER_NAME} pip3 install -r /requirements.txt
   Example: docker exec -it odoo pip3 install -r /requirements.txt

Ejecutar SQL 

   docker exec -it ${PG_CONTAINER_NAME} psql -U ${PG_USER} {NAME_DATABASE}
   Example: docker exec -it postgres psql -U admin deplog

Actualizar módulos

1. Abrir shell 
   docker exec -it ${ODOO_CONTAINER_NAME} sh
   docker exec -it odoo sh
2. Ejecutar comando para actualizar base de datos y módulos
   odoo -d {NAME_DATABASE} -u all --workers=0
   Example: odoo -d deplog -u all --workers=0




Cuando modificas archivos XML (Vistas, Datos, Informes, etc.):

1. Actualización necesaria: Si has realizado cambios en archivos XML, como vistas (.xml), datos (.xml), informes (.xml), etc., necesitarás actualizar el módulo para que esos cambios surtan efecto en tu instancia de Odoo.

2. Procedimiento de actualización: Después de realizar cambios en archivos XML, debes actualizar el módulo utilizando el proceso de actualización estándar de Odoo. Esto puede hacerse a través de la interfaz de usuario de Odoo (actualizando el módulo desde la lista de módulos instalados) o mediante comandos de terminal (odoo -u <nombre_del_módulo>).

Cuando modificas archivos Python (Modelos, Controladores, etc.):

1. Actualización necesaria: Si has realizado cambios en archivos Python (.py), como modelos (models.py), controladores (controllers.py), etc., generalmente no necesitarás actualizar el módulo para que esos cambios surtan efecto en tu instancia de Odoo. Los archivos Python se recargan automáticamente por Odoo cada vez que se detectan cambios.

2. Procedimiento de actualización: Después de realizar cambios en archivos Python, simplemente reinicia el servidor Odoo para que los cambios surtan efecto. Puedes hacerlo mediante el comando de terminal (Compose Restart) o mediante herramientas de administración de servicios según tu configuración. (Los archivos Python se recargan automáticamente por Odoo pero a veces es necesario reiniciar el servidor para que surtan efecto)

NOTAS ADICIONALES:

1. Código JavaScript y CSS: Los cambios en archivos JavaScript (.js) y CSS (.css) generalmente tampoco requieren una actualización del módulo. Los navegadores web cargan estos archivos de forma dinámica y cualquier cambio se reflejará inmediatamente en la interfaz de usuario.

2. Archivos de configuración: Los cambios en archivos de configuración como .yml o .csv pueden requerir una actualización dependiendo de cómo se utilizan en tu implementación. Si modificas archivos de configuración que definen datos iniciales o configuraciones específicas del módulo, es posible que necesites actualizar el módulo para que esos cambios se apliquen correctamente.


REINICIAR EL SERVIDOR:

1. Cambios en archivos Python: Después de realizar cambios en archivos Python (modelos, controladores, etc.), es recomendable reiniciar el servidor para que los cambios surtan efecto. Aunque los archivos Python se recargan automáticamente por Odoo, a veces puede ser necesario reiniciar el servidor para asegurar que los cambios se apliquen correctamente.

2. Actualizaciones de módulos: Después de actualizar un módulo mediante el proceso estándar de actualización de Odoo (-u en el terminal o desde la interfaz de usuario), es necesario reiniciar el servidor para que los cambios en el módulo se apliquen completamente.

3. Instalación de módulos nuevos: Después de instalar nuevos módulos en Odoo, es necesario reiniciar el servidor para que los módulos recién instalados estén disponibles para su uso.

NO REINICIAR EL SERVIDOR:

1. Cambios en archivos XML: Después de realizar cambios en archivos XML (vistas, datos, informes, etc.), generalmente no necesitas reiniciar el servidor. Los cambios en archivos XML se cargan dinámicamente por Odoo y se reflejarán automáticamente en la aplicación sin necesidad de reiniciar el servidor.

2. Actualización de datos en la base de datos: Si estás realizando cambios en la base de datos utilizando la interfaz de administración de Odoo (crear, editar o eliminar registros), no es necesario reiniciar el servidor. Estos cambios se aplican directamente en la base de datos y se reflejarán en la aplicación inmediatamente.

3. Cambios en archivos estáticos: Los cambios en archivos estáticos como JavaScript, CSS o imágenes no requieren reiniciar el servidor. Los navegadores web cargan estos archivos de forma dinámica y cualquier cambio se reflejará inmediatamente en la interfaz de usuario.




