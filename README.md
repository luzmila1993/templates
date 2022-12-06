# templates

Templates Azure Pipeline que serán invocados por el pipeline de la aplicación para la construcción del artefacto.

## ibm-gitops-pre-deploy.yml

Template que se encargará de ejecutar todas las tareas prerrequisito antes de iniciar el proceso de despliegue.


## ibm-gitops-deploy.yml

Template que contiene todas las tareas necesarias para desplegar la aplicación a través del operator de OpenShift GitOps.

## gitops-manifest

Carpeta contendrá todos los charts de Helm necesarios para el despliegue de los Custom Resource.

### integration-server

Carpeta que contiene plantilla Helm de Custom Resource del Integration Server.

El proyecto contempla las siguientes variables:
```yaml
metadata:
  # Nombre del integration server a desplegar
  name: ace-custom-bar-gitops-helm
  # Namespace por defecto donde se desplegara el CR
  namespace: cp4i
```
```yaml
spec:
  # Licencia del integration server
  license: L-KSBM-C87FU2
  # Modo de uso del integration server
  use: CloudPakForIntegrationNonProduction
```
```yaml
# Version del integration server
version: '12.0.2.0-r2'
# URLs de los BAR
barURL: ''
```
```yaml
configuration:
  # Credenciales de acceso a jfrog para poder descargar los artefactos
  credentials: jfrog-credentials
  # Nombre de la politica asociada
  policy: policy-policyname
```
```yaml
resources: {}
```

### policyconfig

Carpeta que contiene la plantilla Helm de Custom Resource del Configuration.

El proyecto contempla las siguientes variables:
```yaml
metadata:
  # Nombre del configuration de tipo policy project a desplegar
  name: policy-helm
  # Namespace por defecto donde se desplegara el CR
  namespace: cp4i
```
```yaml
spec:
  # Base64 del archivo comprimido que contiene el policy project.
  contents: ''
  # Tipo de configuration
  type: policyproject
  # Version del integration server
  version: "12.0.2.0-r2"
```
```yaml
resources: {}
```
