kubectl describe deployment test-deployment | grep Namespace

kubectl logs test-deployment-68f747d97-dnqnk

kubectl expose deployment test-deployment --port=80 --type=NodePort

kubectl get service

open browser naar de port: "This request was processed by host: test-deployment-68f747d97-dnqnk"