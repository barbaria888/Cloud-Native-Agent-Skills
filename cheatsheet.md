# GCP Cloud Native Development — Command Cheatsheet

## Project & Auth
```bash
gcloud auth login
gcloud auth application-default login
export PROJECT_ID=$(gcloud config get project)
gcloud config set project $PROJECT_ID
gcloud config set compute/region $REGION
gcloud config set run/region $REGION
gcloud beta interactive              # interactive shell with completion
```

## Services
```bash
# Enable commonly needed services
gcloud services enable \
  run.googleapis.com \
  cloudbuild.googleapis.com \
  artifactregistry.googleapis.com \
  cloudfunctions.googleapis.com \
  cloudscheduler.googleapis.com \
  secretmanager.googleapis.com \
  container.googleapis.com
```

## IAM / Service Accounts
```bash
gcloud iam service-accounts create $SA_NAME \
  --display-name "$SERVICE display name"

# Add project-level role
gcloud projects add-iam-policy-binding $PROJECT_ID \
  --member=serviceAccount:$SA_NAME@$PROJECT_ID.iam.gserviceaccount.com \
  --role=roles/run.invoker

# Add bucket-level role
gsutil iam ch serviceAccount:$SA_NAME@$PROJECT_ID.iam.gserviceaccount.com:objectViewer \
  gs://$BUCKET_NAME

# List service accounts
gcloud iam service-accounts list
```

## Cloud Storage
```bash
gsutil mb gs://$BUCKET_NAME
gsutil cp $LOCAL_FILE gs://$BUCKET_NAME/$OBJECT
gsutil cat gs://$BUCKET_NAME/$OBJECT | wc -l
gsutil ls gs://$BUCKET_NAME
```

## BigQuery
```bash
bq query --max_rows=10 --nouse_legacy_sql --format=csv "SELECT ..."
bq query --max_rows=100000 --nouse_legacy_sql --format=csv "..." > tags.csv
```

## Cloud Functions (Gen 2)
```bash
# Deploy
gcloud functions deploy $FUNCTION_NAME \
  --gen2 --runtime=go120 --region=$REGION \
  --trigger-http --no-allow-unauthenticated \
  --service-account=$SA_NAME@$PROJECT_ID.iam.gserviceaccount.com \
  --env-vars-file env.yaml

# Call / test
gcloud functions call $FUNCTION_NAME --gen2 --region=$REGION
curl -H "Authorization: Bearer $(gcloud auth print-identity-token)" $FUNCTION_URI

# Logs
gcloud functions logs read $FUNCTION_NAME --gen2 --region=$REGION

# Describe (get URI)
gcloud functions describe $FUNCTION_NAME --gen2 --region=$REGION \
  --format='value(serviceConfig.uri)'
```

## Cloud Scheduler
```bash
gcloud services enable cloudscheduler.googleapis.com

gcloud scheduler jobs create http $JOB_NAME \
  --schedule="0 0 * * SUN" \
  --uri=$FUNCTION_URI \
  --max-retry-attempts=3 \
  --location=$REGION \
  --oidc-service-account-email=$INVOKER_SA@$PROJECT_ID.iam.gserviceaccount.com \
  --oidc-token-audience=$FUNCTION_URI

gcloud scheduler jobs run $JOB_NAME --location=$REGION
gcloud scheduler jobs list --location=$REGION
```

## Cloud Run
```bash
# Deploy from source
gcloud run deploy $SERVICE_NAME --source . \
  --env-vars-file=.env.yaml \
  --no-allow-unauthenticated \
  --service-account=$SA_NAME@$PROJECT_ID.iam.gserviceaccount.com

# Get service URL
export URL=$(gcloud run services describe $SERVICE_NAME --format='value(status.url)')

# Update settings without redeploying
gcloud run services update $SERVICE_NAME --min-instances 1
gcloud run services update $SERVICE_NAME --cpu 2
gcloud run services update $SERVICE_NAME --concurrency 80

# Update service account
gcloud run services update $SERVICE_NAME \
  --service-account $SA_NAME@$PROJECT_ID.iam.gserviceaccount.com

# Logs
gcloud beta run services logs tail $SERVICE_NAME --project $PROJECT_ID
gcloud logging read "resource.labels.service_name: $SERVICE_NAME" --limit 10

# Local dev
gcloud beta code dev
```

## Cloud Build
```bash
# Submit build (creates image)
gcloud builds submit --pack image=$IMAGE_NAME .

# Submit with Dockerfile
gcloud builds submit --tag gcr.io/$PROJECT_ID/$IMAGE_NAME .
```

## Cloud Logging
```bash
# Read logs with filter
gcloud logging read "resource.labels.service_name: $SERVICE_NAME" --limit 10
gcloud logging read "resource.labels.service_name: $SERVICE_NAME AND textPayload: error" \
  --limit 10 --format="value(textPayload)"

# Create log-based metric
gcloud logging metrics create $METRIC_NAME --config-from-file=metric.json
gcloud logging metrics list
```

## Cloud Monitoring
```bash
# Create dashboard from YAML
gcloud monitoring dashboards create --config-from-file=dashboard.yaml

# Create notification channel
gcloud alpha monitoring channels create --channel-content-from-file=channel.yaml

# Create alert policy
gcloud alpha monitoring policies create --policy-from-file=alert.yaml
```

## GKE / Kubernetes
```bash
# Create GKE Autopilot cluster
gcloud container clusters create-auto $CLUSTER_NAME \
  --region=$REGION --project=$PROJECT_ID

# Get credentials
gcloud container clusters get-credentials $CLUSTER_NAME --region=$REGION

# Workload Identity binding
gcloud iam service-accounts add-iam-policy-binding \
  $GSA_NAME@$PROJECT_ID.iam.gserviceaccount.com \
  --role roles/iam.workloadIdentityUser \
  --member "serviceAccount:$PROJECT_ID.svc.id.goog[$NAMESPACE/$KSA_NAME]"

kubectl annotate serviceaccount $KSA_NAME \
  --namespace $NAMESPACE \
  iam.gke.io/gcp-service-account=$GSA_NAME@$PROJECT_ID.iam.gserviceaccount.com

# Common kubectl
kubectl get pods
kubectl get services
kubectl get nodes
kubectl describe pod $POD_NAME
kubectl logs $POD_NAME
kubectl apply -f deployment.yaml
kubectl delete -f deployment.yaml
```

## Skaffold (Inner Loop)
```bash
skaffold init --generate-manifests
skaffold build
skaffold run --port-forward
skaffold dev                    # watch mode: rebuild+redeploy on save
skaffold debug                  # debug mode with breakpoints
```

## Terraform
```bash
terraform init
terraform plan -var project_id=$PROJECT_ID
terraform apply -var project_id=$PROJECT_ID
terraform destroy
```

## Secret Manager
```bash
# Create secret
echo -n "my-secret-value" | gcloud secrets create $SECRET_NAME --data-file=-

# Grant access
gcloud secrets add-iam-policy-binding $SECRET_NAME \
  --member=serviceAccount:$SA_NAME@$PROJECT_ID.iam.gserviceaccount.com \
  --role=roles/secretmanager.secretAccessor

# Access secret value
gcloud secrets versions access latest --secret=$SECRET_NAME
```

## Performance Testing
```bash
# Apache Bench
ab -n 100 -c 1 -rk "$URL/endpoint"     # 100 requests, 1 concurrent
ab -n 100 -c 10 -rk "$URL/endpoint"    # 100 requests, 10 concurrent

# Install on Cloud Shell
sudo apt-get install apache2-utils
```

## Billing
```bash
gcloud beta billing accounts list
export BILLING_ID=[ID]
gcloud beta billing projects link $PROJECT_ID --billing-account $BILLING_ID
gcloud beta billing projects describe $PROJECT_ID --format="value(billingEnabled)"
gcloud beta billing projects unlink $PROJECT_ID   # stops charges
```
