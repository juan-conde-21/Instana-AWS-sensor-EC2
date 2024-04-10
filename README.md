# Despliegue de Instana sensor para AWS en servicio EC2


1. Crear la siguiente politica IAM en AWS.


  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/01ac6403-4a6f-43a3-a85c-89dddd1d06eb)

2. Seleccionar JSON y luego pegar la siguiente definición de política.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/4ac24155-1c5b-4014-af39-acbe7e57083e)

        {
        "Version": "2012-10-17",
        "Statement": [
          {
            "Action": [
              "elasticbeanstalk:DescribeEnvironments",
              "elasticbeanstalk:ListTagsForResource",
              "elasticbeanstalk:DescribeInstancesHealth",
              "dynamodb:ListTables",
              "dynamodb:DescribeTable",
              "dynamodb:ListTagsOfResource",
              "rds:DescribeDBInstances",
              "rds:DescribeEvents",
              "rds:ListTagsForResource",
              "sqs:ListQueues",
              "sqs:GetQueueAttributes",
              "sqs:ListQueueTags",
              "elasticache:ListTagsForResource",
              "elasticache:DescribeCacheClusters",
              "elasticache:DescribeEvents",
              "elasticloadbalancing:DescribeLoadBalancers",
              "elasticloadbalancing:DescribeTags",
              "elasticmapreduce:ListClusters",
              "elasticmapreduce:DescribeCluster",
              "es:ListDomainNames",
              "es:DescribeElasticsearchDomain",
              "es:ListTags",
              "ec2:DescribeInstances",
              "ec2:DescribeTags",
              "ec2:DescribeVolumes",
              "kafka:ListClusters",
              "kafka:ListNodes",
              "kafka:ListTagsForResource",
              "kafka:DescribeCluster",
              "kinesis:ListStreams",
              "kinesis:DescribeStream",
              "kinesis:ListTagsForStream",
              "lambda:ListTags",
              "lambda:ListFunctions",
              "lambda:ListVersionsByFunction",
              "lambda:ListEventSourceMappings",
              "lambda:GetFunctionConfiguration",
              "mq:ListBrokers",
              "mq:DescribeBroker",
              "s3:GetBucketTagging",
              "s3:ListAllMyBuckets",
              "s3:GetBucketLocation",
              "xray:BatchGetTraces",
              "xray:GetTraceSummaries",
              "tag:GetResources"
            ],
            "Effect": "Allow",
            "Resource": "*"
          },
          {
            "Action": [
              "cloudwatch:GetMetricStatistics",
              "cloudwatch:GetMetricData",
              "cloudwatch:ListMetrics"
            ],
            "Effect": "Allow",
            "Resource": "*"
          }
        ]
        }

3. Seleccionar Next, luego completar el nombre y seleccionar "Create policy"

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/bed37427-3dd3-487b-8f01-37308757300d)
  
  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/3a03c946-5c63-4fb5-a60b-c0ea3586b9ff)
  
  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/107815e4-736a-40a1-9bca-4f178020f9b3)


4. Verificar la politica creada filtrando por nombre.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/20fa6ab8-67af-4006-98ae-23f010647184)

5. Crear el rol que sera asignado al servicio EC2 donde se instalará el agente de Istana.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/1a281cb4-ac8e-4b55-a70e-aeddda0fb071)

6. Seleccionar el servicio EC2 y luego continuar con Next.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/fb216b2d-0b37-491d-b56d-dcccdc330f97)


7. En la siguiente pantalla buscar y seleccionar la política creada en los pasos anteriores y continuar seleccionando Next.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/0e86afd5-c50c-40a9-bacf-2624b79e22d4)

8. Colocar el nombre del rol, verificar los permisos otorgados en el paso anterior y seleccionar "Create role" para crear el nuevo rol.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/22a36c8a-0bb2-4f3a-9a59-5f7c90d85439)

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/2d138e92-130f-40cf-99ab-f23badc11ba4)

9. Verificar el nuevo rol creado en la consola IAM.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/e3265c2b-408d-4e05-a958-3da19fc2e28d)

10. Despliegue de instancia EC2.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/a6908561-cc3a-4996-aff6-7f4711b3a19a)

11. Colocar el nombre, asociar el rol creado en los pasos previos y seleccionar el tipo de instancia EC2.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/be2c711a-a40a-4b4f-aa5b-c337f9ac9439)

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/a3d6efe2-8321-46cd-9c10-1c627be264eb)

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/9ffbc74d-b4d2-4cea-95cf-ab65880b73ce)


12. Ingresar a la consola de Instana y acceder a la seccion de agentes.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/c4d29f27-dc8d-4ce6-87c7-23a5e9522069)


13. En el módulo de agentes ingresar al catálogo para el despliegue del agente Instana.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/3b36b585-edde-46f2-9294-99b3a758e84d)

14. Buscar los agentes para AWS y seleccionar "Instana AWS Sensor".

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/c6636aff-684d-4cdb-b8a3-48a1a85ec30a)

15. En esta sección obtendremos los comandos de instalación del agente Instana, que será utilizado para la instalación en la instancia EC2 creada en los pasos previos.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/fe8167f4-3518-4b51-8a98-b19d0f7c6d31)

16. Ingresar a la instancia EC2 con permisos de root y ejecutar los comandos de instalación del paso anterior, al finalizar se indicará que el servicio del agente se habilitó e inicio como se muestra en la siguiente imagen.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/97be709a-d804-4c9a-a6d0-abbf9e5d1144)

  *Con esta configuracion base se realizara el monitoreo de los servicios pertenecientes a la misma region donde se encuentra desplegada la instancia EC2, en caso se requieran regiones adicionales se debe realizar el despliegue de una       instancia por cada region.

17. En caso se requiera modificar la configuración del agente para realizar un filtrado de servicios en base a tags o agregar parametros adicionales, detener el agente y proceder con la configuracion a nivel del archivo cofiguration.yaml

  Detener agente y validar estado del servicio:

    systemctl stop instana-agent
    systemctl status instana-agent

  Ejemplo de ejecución:

    [root@ip-172-31-31-231 ~]# systemctl stop instana-agent
    [root@ip-172-31-31-231 ~]# systemctl status instana-agent
    ○ instana-agent.service - "Instana(tm) agent."
         Loaded: loaded (/usr/lib/systemd/system/instana-agent.service; enabled; preset: disabled)
        Drop-In: /etc/systemd/system/instana-agent.service.d
                 └─agent-custom-start.conf, custom-environment.conf
         Active: inactive (dead) since Tue 2024-04-09 23:00:26 UTC; 6s ago
       Duration: 17.891s
        Process: 3213 ExecStart=/opt/instana/agent/bin/karaf daemon (code=exited, status=0/SUCCESS)
        Process: 3329 ExecStop=/opt/instana/agent/bin/karaf stop (code=exited, status=0/SUCCESS)
       Main PID: 3213 (code=exited, status=0/SUCCESS)
            CPU: 23.796s
    
    Apr 09 23:00:21 ip-172-31-31-231.us-west-2.compute.internal karaf[3213]:         at org.apache.karaf.features.internal.service.Deployer.deploy(Deployer.java:908)
    Apr 09 23:00:21 ip-172-31-31-231.us-west-2.compute.internal karaf[3213]:         at org.apache.karaf.features.internal.service.FeaturesServiceImpl.doProvision(FeaturesServiceImpl.java:1063)
    Apr 09 23:00:21 ip-172-31-31-231.us-west-2.compute.internal karaf[3213]:         at org.apache.karaf.features.internal.service.FeaturesServiceImpl.lambda$doProvisionInThread$13(FeaturesServiceImpl.java:998)
    Apr 09 23:00:21 ip-172-31-31-231.us-west-2.compute.internal karaf[3213]:         at java.util.concurrent.FutureTask.run(FutureTask.java:266)
    Apr 09 23:00:21 ip-172-31-31-231.us-west-2.compute.internal karaf[3213]:         at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
    Apr 09 23:00:21 ip-172-31-31-231.us-west-2.compute.internal karaf[3213]:         at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
    Apr 09 23:00:21 ip-172-31-31-231.us-west-2.compute.internal karaf[3213]:         at java.lang.Thread.run(Thread.java:750)
    Apr 09 23:00:26 ip-172-31-31-231.us-west-2.compute.internal systemd[1]: instana-agent.service: Deactivated successfully.
    Apr 09 23:00:26 ip-172-31-31-231.us-west-2.compute.internal systemd[1]: Stopped instana-agent.service - "Instana(tm) agent.".
    Apr 09 23:00:26 ip-172-31-31-231.us-west-2.compute.internal systemd[1]: instana-agent.service: Consumed 23.796s CPU time.


18. Para realizar el filtrado de servicios en base al tag del servicio AWS, ingresar a la ruta de configuracion del agente y editar el archivo configuration.yaml 

    - Ingresar a la siguiente ruta "/opt/instana/agent/etc/instana"

      Ejemplo:

          cd /opt/instana/agent/etc/instana


    - Editar el archivo configuration.yaml

      Ejemplo:

          vi configuration.yaml

    - Ubicar las líneas para el filtrado por tag y proceder a descomentarlas, se muestra la configuración que consulta los tags cada 60 segundos e incluye los servicios con el tag "env:POC" y excluye los servicios que no tienen tag
   
      Ejemplo:

          com.instana.plugin.aws:
            tagged-services-poll-rate: 60
            include_tags: env:POC
          #  exclude_tags:
            include_untagged: false

      ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/d1f7cd51-0b2a-4720-991f-fba082d0cb4e)

      *Tambien se puede realizar una configuración personalizada por cada servicio.

    - Reiniciar los servicios del agente para aplicar las modificaciones realizadas.

      Ejemplo:

          systemctl restart instana-agent

19. Luego de reiniciar los servicios verificar en la consola de instana, en la sección de Infratructure colocar el filtro por tipo de entidad y tag como se muestra en la siguiente imagen.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/c067fa26-e8a7-45e1-ba8b-4dfbf90c1770)


20. Tambien es posible acceder desde el módulo de Analytics --> Infratructure.

  ![image](https://github.com/juan-conde-21/Instana-sensor-AWS-EC2/assets/13276404/484ebeae-eb40-41c8-952d-054cd66daab0)













