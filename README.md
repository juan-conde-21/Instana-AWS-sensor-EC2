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

9. 

  










