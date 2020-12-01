# elecciones

## Armado ambiente desarrollo (Automático)
ToDo

## Armado ambiente desarrollo (Manual)

Requerimientos:
- Wildfly 20.0.1
- Eclipse JEE o IDE similar
- Postgresql 9.6 o 10.x
- Maven 3.6

### Wildlfy modules
Es necesario instalar en Wildfly los módulos:
- `net.ipresource`
- `jxl`

Estos módulos están incluídos en este reporitorio, en la carpeta `config/modules`.
Para instalarlos en Wildfly basta con copiar los módulos en la raíz de la carpeta `$WILDFLY_HOME/modules`.

### Wildlfy drivers
Es necesario publicar en Wildfly el driver JDBC de postgreSQL:
- `postgresql-42.2.16.jar`

Para publicarlo basta con copiar el archivo (descargarlo del sitio de postgresql/downloads) en `$WILDFLY_HOME/standalone/deployments`.

### Database restore
ToDo

### Wildlfy datasource
Es necesario publicar en Wildfly el datasource de la aplicación, con las credenciales y datos de acceso a la base de datos. Hay un datasource de ejemplo dentro de la carpeta `config/ds`.
Para publicarlo basta con copiar el archivo en `$WILDFLY_HOME/standalone/deployments`.

### Wildlfy management console access
Es necesario configurar en Wildfly un usuario de la consola de administración, a través de la cual se hacen los deployments de los proyectos.

Para crear un usuario utilizar los scripts `add-user.bat`/`add-user.sh` ubicados en `WILDFLY_HOME/bin`.

### Build proyectos Maven

Para compilar los proyectos se utiliza maven, se pueden configurar los goals `clean compile install package` en el IDE para compilar y empaquetar los binarios.

### Deploy local

Para publicar los proyectos en el Wildfly local (levantado), se utiliza el plugin de wildlfy para maven. Para disparar el deploy (luego del package), ejecutar:
    
    mvn wildfly:deploy
