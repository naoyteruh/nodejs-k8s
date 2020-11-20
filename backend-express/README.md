
gcloud services enable cloudbuild.googleapis.com

gcloud services enable container.googleapis.com

sudo apt-get install kubectl

gcloud projects list

gcloud config set project nodejs-k8s-295722

gcloud config get-value project

cd nodejs-k8s/backend-express

gcloud builds submit --tag gcr.io/nodejs-k8s-295722/helloworld-gke .

gcloud container clusters create helloworld-gke \
   --num-nodes 1 \
   --enable-basic-auth \
   --issue-client-certificate \
   --zone europe-west1-b

kubectl apply -f deployment.yaml 

kubectl get deployments
kubectl get pods

(
kubectl delete pod helloworld-gke-668fbf9758-9g4hz
kubectl delete deployment helloworld-gke
)

kubectl apply -f service.yaml

kubectl get services

curl <EXTERNAL-IP>

gcloud container clusters delete helloworld-gke --zone europe-west1-b
gcloud container images delete gcr.io/nodejs-k8s-295722/helloworld-gke
