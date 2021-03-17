# Samaritan

![Version: 0.1.0-alpha](https://img.shields.io/badge/Version-0.1.0--alpha-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

[Samaritan](https://samaritan.works) is a vulnerability discovery metrics collection and analysis platform. The platform is being developed as part of the _Human Dimensions of Software Engineering Processes_ project funded by the Defense Advanced Research Projects Agency (DARPA) under a Small Business Innovation Research (SBIR) grant.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| image.pullSecrets | list | `[]` | List of secret names to use when attempting to access private container image registries. The secrets are _assumed_ to be existing in the namespace into which the chart will be installed. |
| ingress.hostname.api | string | `"api.samaritan.works"` | URL to use for the Samaritan API Service endpoint. |
| ingress.hostname.web | string | `"explore.samaritan.works"` | URL to use for the Samaritan Web Application endpoint. |
| ingress.provider | string | `"public"` | Ingress provider to use to provision publicly accessible URLs for services. Must be one of `public` for [NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/) or `alb` for [AWS Load Balancer Controller](https://kubernetes-sigs.github.io/aws-load-balancer-controller/latest/). |
| mysql.application.password | string | `nil` | **[Required]** MySQL application password. The services that need to persist data to a MySQL database will use this as the password. |
| mysql.application.user | string | `"samaritan"` | MySQL application user. The services that need to persist data to a MySQL database will use this as the user. |
| mysql.external | bool | `false` | Set to `true` if you wish you use a MySQL instance provisioned outside of the Kubernetes deployment. |
| mysql.externalName | string | `""` | URL of the external MySQL instance. |
| mysql.port | int | `3306` | MySQL port. |
| mysql.root.password | string | `nil` | **[Required]** MySQL root password. |
| rabbitmq.external | bool | `false` | Set to `true` if you wish you use a RabbitMQ instance provisioned outside of the Kubernetes deployment. |
| rabbitmq.externalName | string | `""` | URL of the external RabbitMQ instance. |
| rabbitmq.password | string | `nil` | **[Required]** RabbitMQ application password. The services that use RabbitMQ for communication will use this as the password. |
| rabbitmq.port | int | `5672` | RabbitMQ port. |
| rabbitmq.protocol | string | `"amqp"` | URI scheme to use when connecting to RabbitMQ. Must be one of `amqp` for an unsecure connection or `amqps` for a secure connection. |
| rabbitmq.user | string | `"samaritan"` | RabbitMQ application user. The services that use RabbitMQ for communication will use this as the user. |
| redis.password | string | `nil` | **[Required]** Redis application password. The services that use Redis for caching will use this as the password. |
| registry | string | `"110921400520.dkr.ecr.us-east-2.amazonaws.com"` | Container registry from which all images are pulled. |
| storage.provider | string | `"local"` | Storage provider to use for persistent storage in stateful services. Must be one of `local` for volume backed by [`hostPath`](https://kubernetes.io/docs/concepts/storage/volumes/#hostpath) or `efs` for volume backed by Amazon Elastic File System. |
| storage.providers.efs.fileSystemId | string | `""` | Unique identifier assigned to the Amazon Elastic File System (EFS). |
| storage.providers.local.root | string | `"/data/"` | Absolute path of the directory on the node that will host the Kubernetes pods that will form the root of the persistent volume mapped onto the pods. |
