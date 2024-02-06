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




