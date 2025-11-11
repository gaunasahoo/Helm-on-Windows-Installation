# Helm-on-Windows-Installation
✅ 1. Install Helm on Windows (PowerShell method — recommended)
winget install Helm.Helm

If winget is not available, install manually:

Go to: https://github.com/helm/helm/releases 
Download helm-vX.X.X-windows-amd64.zip
Extract → You will get helm.exe
Move helm.exe to path:
C:\Program Files\helm\

Add this folder to Environment Variables → PATH

✅ 2. Verify Helm Installation
helm version

✅ 3. Add Litmus Chaos Helm Repository
helm repo add litmuschaos https://litmuschaos.github.io/litmus-helm/
helm repo update

✅ 4. Install Litmus Chaos Using Helm
Install Litmus Chaos Control Plane
helm install litmus litmuschaos/litmus --namespace litmus --create-namespace

This installs:
✅ ChaosCenter (UI)
✅ ChaosOperator
✅ Event tracker
✅ Exporter

✅ 5. Get ChaosCenter UI URL

If using AKS:
kubectl -n litmus get svc chaos-litmus-frontend-service

Use the EXTERNAL-IP to open Litmus in the browser.

If you are using NodePort cluster (minikube):
minikube service -n litmus chaos-litmus-frontend-service --url

✅ 6. Default Login for ChaosCenter

Username: admin

Password: litmus

✅ 7. Common Helm Errors & Fixes
✅ “sudo is disabled on this machine”

Ignore — you are on Windows.
Use PowerShell, not Git Bash.

✅ “helm is not recognized”

Add helm to path:
setx PATH "$Env:PATH;C:\Program Files\helm"
Restart PowerShell.




