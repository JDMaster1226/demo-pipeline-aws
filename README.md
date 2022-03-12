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

 ## 2. Configuración
Crear el pipeline con la herramienta **codePipeline** y se selecciona el rol creado anteriormente

![](./img/4.png)

Se procede a realizar la conexión del repositorio de gitHub, como se muestra a continuación

![](./img/5.png)
 
Para la configuración de cloudformation se necesita la plantilla creada llamada **demoAWS.json** y el rol llamado **cloudformation_s3** creado anteriormente

![](./img/6.png)

A continuación podemos evidenciar el resumen de la configutacion creada y la creación del pipeline.

![](./img/7.png)

Para que funcione correctamente se debe agregar el siguiente permiso a cada rol

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "codestar-connections:UseConnection",
            "Resource": "arn:aws:codestar-connections:sa-east-1:244937477184:connection/69b25c8e-7afe-47de-b963-5d55817e8751"
        }
    ]
}
```

El pipeline se empezara a ejecutar y debe salir exitosa como se muestra a continuación

![](./img/8.png)

Cada vez que se actualiza la rama, se puede evidenciar que se realiza el deploy automatico. 

![](./img/9.png)

![](./img/10.png)


**Se utilizaron las tecnologias descritas anteriormente principalmente porque son las tecnologias en las cuales tengo mas conocimiento, aclarando que AWS CloudFormation y Jenkins son muy utilizadas y con ambas se lograria una buena implementacion de automatización.**
