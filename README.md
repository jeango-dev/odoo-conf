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

Instalar dependencias del requirements:

1. Copiar Dependencias al Contenedor
   docker cp requirements.txt ${ODOO_CONTAINER_NAME}:/requirements.txt
   docker cp requirements.txt odoo15:/requirements.txt

2. Instalar Dependencias
   docker exec -it ${ODOO_CONTAINER_NAME} pip3 install -r /requirements.txt
   docker exec -it odoo15 pip3 install -r /requirements.txt


