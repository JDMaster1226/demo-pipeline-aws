# Integración continua con AWS - CloudFormation 

A continuación se muestra un ejemplo basico de una infraestructura creada para AWS con una integracion continua por medio de la implementacion de CloudFormation.

## 1. Creación de Roles
Como primer paso se crearon dos Roles, los cuales se describen a continuación:

**pipeline_role_juan**: Este corresponde a los permisos que necesita el Pipeline correspondiente a la herramienta de AWS

![](./img/1.jpg)

El rol de pipeline necesita permisos adicionales, el cual con esta configuracion de json se añaden dichos permisos, como se ve en la siguiente imagen:

![](./img/2.png)

El siguiente rol a crear es el de **cloudformation** el cual nos permite hacer el deploy automatico.

![](./img/3.png)

