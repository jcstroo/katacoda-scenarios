
# Controleer de omgeving
Omdat het even duurt voordat alles klaar staat, kan je onderstaande commando gebruiken om te zien of de omgeving al klaar is:
`while [ ! -f /root/.kube/config ]; do sleep 5 && echo "nog even geduld..."; done && echo "We kunnen verder!"`{{execute}}

## namespaces
Een namespace is een onderdeel van de isolatie binnen Kubernetes. We kijken eerst naar de huidige namespaces: `kubectl get namespaces`{{execute}}

Nu maken we er een paar bij:
`kubectl create namespace test1`{{execute}}
`kubectl create namespace test2`{{execute}}

Deze worden nu zichtbaar in het overzicht: `kubectl get namespaces`{{execute}}
