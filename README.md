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
   docker cp requirements.txt odoo:/requirements.txt
2. Instalar Dependencias
   docker exec -it ${ODOO_CONTAINER_NAME} pip3 install -r /requirements.txt
   docker exec -it odoo pip3 install -r /requirements.txt

Ejecutar SQL 

   docker exec -it ${PG_CONTAINER_NAME} psql -U ${PG_USER} {NAME_DATABASE}
   docker exec -it postgres psql -U admin deplog_v15

Actualizar módulos

1. Abrir shell 
   docker exec -it nombre_del_contenedor_odoo sh
   docker exec -it odoo sh
2. Ubicarse en carpeta de odoo-bin
   cd var/lib/odoo/odoo
3. Instalar dos2unix 
   apt-get update
   apt-get install dos2unix
4. Ejecutar dos2unix en odoo-bin
   dos2unix odoo-bin
5. Actualizar módulos
   ./odoo-bin -d nombre_de_tu_base_de_datos -u all --workers=0
   ./odoo-bin -d deplog -u all --workers=0




