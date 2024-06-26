# Configuración de service account para autenticar Terraform con GCP

-   Ver el [siguiente video](https://youtu.be/KilW1B8gxW4?si=EyeC7kTnZO5Otjzr) que explica como crear la service account y obtener las keys en formato `.json`.
-   Copiar el archivo descargado en el directorio raíz y renombrarlo a `credentials.json`.
-   Otorgarle permisos de 'Editor' a la service account en la sección de IAM de GCP console.

## Creación de infraestructura para workers

-   Ejecutar terraform para crear la instancia de la VM en GCP.

```bash
BUCKET_NAME="terraform_state_cloud"
PREFIX="workers/state"
terraform init --reconfigure --backend-config "bucket=${BUCKET_NAME}" --backend-config "prefix=${PREFIX}"
terraform plan -lock=false
terraform apply -lock=false --auto-approve
```
