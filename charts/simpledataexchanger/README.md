# sde

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 3.0.0](https://img.shields.io/badge/AppVersion-3.0.0-informational?style=flat-square)

A Helm chart for simple data exchanger

## Source Code

* <https://github.com/eclipse-tractusx/managed-simple-data-exchanger>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | sdepostgresql(postgresql) | 12.x.x |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| backend.affinity | object | `{}` |  |
| backend.autoscaling.enabled | bool | `false` |  |
| backend.autoscaling.maxReplicas | int | `100` |  |
| backend.autoscaling.minReplicas | int | `1` |  |
| backend.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| backend.backend.endpoints.default.path | string | `"/"` | The path mapping the "default" api is going to be exposed at |
| backend.backend.endpoints.default.port | int | `7070` | The network port, which the "default" api is going to be exposed by the container, pod and service |
| backend.configuration.properties | string | `"keycloak.clientid=CX-SDE\nspring.security.oauth2.resourceserver.jwt.issuer-uri=default\nmanagement.endpoint.health.probes.enabled=true\nmanagement.health.readinessstate.enabled=true\nmanagement.health.livenessstate.enabled=true\nmanagement.endpoints.web.exposure.include=*\nspring.lifecycle.timeout-per-shutdown-phase=30s\nlogging.level.org.springframework.security.web.csrf=DEBUG\nspring.servlet.multipart.enabled=true\nspring.main.allow-bean-definition-overriding=true\nspring.servlet.multipart.file-size-threshold=2KB\nspring.servlet.multipart.max-file-size=200MB\nspring.servlet.multipart.max-request-size=215MB\nserver.servlet.context-path=/api\nspring.flyway.baseline-on-migrate=true\nspring.flyway.locations=classpath:/flyway\nspring.datasource.driver-class-name=org.postgresql.Driver\nspring.jpa.hibernate.ddl-auto=update\nspring.jpa.open-in-view=false\nfile.upload-dir=./temp/\nlogging.level.org.apache.http=debug\nlogging.level.root=debug\ndigital-twins.hostname=default\ndigital-twins.authentication.url=default\ndigital-twins.registry.uri=/api/v3\ndigital-twins.registry.lookup.uri=/api/v3\ndigital-twins.authentication.clientId=default\ndigital-twins.authentication.clientSecret=default\ndigital-twins.authentication.grantType=client_credentials\nedc.hostname=default\nedc.managementpath=/management\nedc.apiKeyHeader=X-Api-Key\nedc.apiKey=default\nedc.dsp.endpointpath=/api/v1/dsp\nedc.dataplane.endpointpath=/api/public\nedc.managementpath.apiversion=/v3\nedc.managementpath.apiversion.asset=/v3\nedc.consumer.hostname=default\nedc.consumer.apikeyheader=X-Api-Key\nedc.consumer.apikey=default\nedc.consumer.managementpath=/management\nedc.consumer.protocol.path=/api/v1/dsp\ndft.hostname=default\ndft.apiKeyHeader=default\ndft.apiKey=default\nmanufacturerId=default\npartner.pool.hostname=default\npartner.pool.authentication.url=default\npartner.pool.clientId=default\npartner.pool.clientSecret=default\npartner.pool.grantType=client_credentials\nbpdm.provider.edc.dsp.api=default\nbpdm.provider.bpnl=default\nportal.backend.hostname=default\nportal.backend.authentication.url=default\nportal.backend.clientId=default\nportal.backend.clientSecret=default\nportal.backend.grantType=client_credentials\nbpndiscovery.hostname=default\ndiscovery.authentication.url=default\ndiscovery.clientId=sdefault\ndiscovery.clientSecret=default\ndiscovery.grantType=client_credentials\nspringdoc.api-docs.path=/api-docs\npolicy.hub.hostname=default\npolicy.hub.authentication.url=default\npolicy.hub.clientId=default\npolicy.hub.clientSecret=default\npolicy.hub.grantType=client_credentials\nmanagement.endpoints.web.exposure.include=*\nmanagement.endpoint.health.show-details=always\nmanagement.metrics.export.prometheus.enabled=true\nmanagement.endpoint.prometheus.enabled=true\nspring.sleuth.sampler.probability=1.0\nspring.zipkin.base-url=http://localhost:9411/\nspring.zipkin.sender.type=web\nspring.application.name=springboot-monitoring-SDE\n#bpdm.provider.edc.dataspace.api=default\nbpdm.provider.bpnl=default\n#bpdm.provider.edc.public.api=default"` |  |
| backend.fullnameOverride | string | `""` |  |
| backend.image.pullPolicy | string | `"Always"` |  |
| backend.image.repository | string | `"tractusx/managed-simple-data-exchanger-backend"` |  |
| backend.image.tag | string | `""` |  |
| backend.imagePullSecrets | list | `[]` |  |
| backend.ingresses[0].annotations."cert-manager.io/cluster-issuer" | string | `nil` |  |
| backend.ingresses[0].annotations."nginx.ingress.kubernetes.io/cors-allow-credentials" | string | `"true"` |  |
| backend.ingresses[0].annotations."nginx.ingress.kubernetes.io/cors-allow-methods" | string | `"PUT, GET, POST, OPTIONS"` |  |
| backend.ingresses[0].annotations."nginx.ingress.kubernetes.io/cors-allow-origin" | string | `"https://*tx.test"` |  |
| backend.ingresses[0].annotations."nginx.ingress.kubernetes.io/enable-cors" | string | `"true"` |  |
| backend.ingresses[0].className | string | `""` |  |
| backend.ingresses[0].enabled | bool | `true` |  |
| backend.ingresses[0].endpoints[0] | string | `"default"` |  |
| backend.ingresses[0].hostname | string | `"sde-backend.tx.test"` |  |
| backend.ingresses[0].hosts | list | `["sde-backend.tx.test"]` | If present overwrites the default secret name certManager:   # -- If preset enables certificate generation via cert-manager namespace scoped issuer   issuer: "letsencrypt-prod"   # -- If preset enables certificate generation via cert-manager cluster-wide issuer   clusterIssuer: "letsencrypt-prod" |
| backend.ingresses[0].tls.enabled | bool | `true` |  |
| backend.nameOverride | string | `""` |  |
| backend.nodeSelector | object | `{}` |  |
| backend.podAnnotations | object | `{}` |  |
| backend.podSecurityContext | object | `{}` |  |
| backend.portContainer | int | `8080` |  |
| backend.resources.limits.cpu | string | `"600m"` |  |
| backend.resources.limits.memory | string | `"2Gi"` |  |
| backend.resources.requests.cpu | string | `"600m"` |  |
| backend.resources.requests.memory | string | `"2Gi"` |  |
| backend.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| backend.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| backend.securityContext.runAsNonRoot | bool | `true` |  |
| backend.securityContext.runAsUser | int | `1001` |  |
| backend.service.port | int | `7070` |  |
| backend.service.targetPort | int | `8080` |  |
| backend.service.type | string | `"ClusterIP"` |  |
| backend.tolerations | list | `[]` |  |
| frontend.affinity | object | `{}` |  |
| frontend.autoscaling.enabled | bool | `false` |  |
| frontend.autoscaling.maxReplicas | int | `100` |  |
| frontend.autoscaling.minReplicas | int | `1` |  |
| frontend.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| frontend.env[0].name | string | `"REACT_APP_API_URL"` |  |
| frontend.env[0].value | string | `"https://sde-backend.tx.test/api"` |  |
| frontend.env[1].name | string | `"REACT_APP_KEYCLOAK_URL"` |  |
| frontend.env[1].value | string | `"https://centralidp.tx.test/auth"` |  |
| frontend.env[2].name | string | `"REACT_APP_KEYCLOAK_REALM"` |  |
| frontend.env[2].value | string | `"CX-Central"` |  |
| frontend.env[3].name | string | `"REACT_APP_CLIENT_ID"` |  |
| frontend.env[3].value | string | `"CX-SDE"` |  |
| frontend.env[4].name | string | `"REACT_APP_FILESIZE"` |  |
| frontend.env[4].value | string | `"104857600"` |  |
| frontend.env[5].name | string | `"REACT_APP_DEFAULT_COMPANY_BPN"` |  |
| frontend.env[5].value | string | `nil` |  |
| frontend.fullnameOverride | string | `""` |  |
| frontend.image.pullPolicy | string | `"Always"` |  |
| frontend.image.repository | string | `"tractusx/managed-simple-data-exchanger-frontend"` |  |
| frontend.image.tag | string | `""` |  |
| frontend.imagePullSecrets | list | `[]` |  |
| frontend.ingresses[0].annotations."cert-manager.io/cluster-issuer" | string | `nil` |  |
| frontend.ingresses[0].className | string | `""` |  |
| frontend.ingresses[0].enabled | bool | `true` |  |
| frontend.ingresses[0].endpoints[0] | string | `"default"` |  |
| frontend.ingresses[0].hostname | string | `"sde.tx.test"` |  |
| frontend.ingresses[0].hosts[0] | string | `"sde.tx.test"` |  |
| frontend.ingresses[0].tls.enabled | bool | `true` |  |
| frontend.nameOverride | string | `""` |  |
| frontend.nodeSelector | object | `{}` |  |
| frontend.podAnnotations | object | `{}` |  |
| frontend.podSecurityContext | object | `{}` |  |
| frontend.portContainer | int | `8080` |  |
| frontend.resources.limits.cpu | string | `"600m"` |  |
| frontend.resources.limits.memory | string | `"2Gi"` |  |
| frontend.resources.requests.cpu | string | `"600m"` |  |
| frontend.resources.requests.memory | string | `"2Gi"` |  |
| frontend.sde.endpoints.default.path | string | `"/"` | The path mapping the "default" api is going to be exposed at |
| frontend.sde.endpoints.default.port | string | `"80"` | The network port, which the "default" api is going to be exposed by the container, pod and service |
| frontend.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| frontend.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| frontend.securityContext.runAsNonRoot | bool | `true` |  |
| frontend.securityContext.runAsUser | int | `101` |  |
| frontend.service.port | int | `80` |  |
| frontend.service.targetPort | int | `8080` |  |
| frontend.service.type | string | `"ClusterIP"` |  |
| frontend.tolerations | list | `[]` |  |
| replicaCount | int | `1` |  |
| sdepostgresql.auth.database | string | `"sdedb"` |  |
| sdepostgresql.auth.existingSecret | string | `""` |  |
| sdepostgresql.auth.password | string | `"password"` |  |
| sdepostgresql.auth.port | int | `5432` |  |
| sdepostgresql.auth.postgresPassword | string | `""` |  |
| sdepostgresql.auth.username | string | `"sdeuser"` |  |
| sdepostgresql.enabled | bool | `true` |  |
| sdepostgresql.fullnameOverride | string | `"product-sde-postgres"` |  |
| sdepostgresql.image | object | `{"repository":"bitnamilegacy/postgresql"}` | PostgreSQL chart configuration Switch to enable or disable the PostgreSQL helm chart |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
