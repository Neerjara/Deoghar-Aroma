# Aroma Deoghar storefront

A static perfume storefront for a Deoghar boutique. Replace the placeholder WhatsApp number `919999999999` in `index.html` and `app.js` before public launch.

## Deploy to the AKS environment

```powershell
az aks get-credentials --resource-group savings-rg --name savings-aks --overwrite-existing
az acr login --name savingswsaacr

docker build -t savingswsaacr.azurecr.io/aroma-deoghar:1.0.0 .
docker push savingswsaacr.azurecr.io/aroma-deoghar:1.0.0

kubectl create namespace storefront
kubectl apply -f k8s/perfume-store.yaml
kubectl get service -n storefront --watch
```

When the service receives an external IP, open `http://<EXTERNAL-IP>`.