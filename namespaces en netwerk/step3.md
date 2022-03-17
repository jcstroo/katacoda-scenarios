
# Het netwerk in een namespace
binnen kubernetes wordt op basis van een CNI-plug-in een virtueel (overlay) netwerk gemaakt. Dit werkt zelfs over nodes heen. Dus ook in een cluster met meerdere nodes heb een virtueel netwerk. Hier hoef je niets voor te doen.

Geef het volgende commando om meer informatie over je pods te zien: `kubectl get pod -n test1 -o wide`{{execute}}
Doe hetzelfde voor de andere namespace: `kubectl get pod -n test2 -o wide`{{execute}}

**Schrijf het IP adres van de eerste pod die hoort bij deployment test-deployment1 op!**

Je ziet dat de pods allemaal een (opvolgend) IP adres hebben gekregen. Dat is de default werking van kubernetes: het virtuele netwerk werkt over alle namespace heen. Je kan dit ook aanpassen, met netwerk isolatie per namespace. Dat is voor nu buiten scope van deze training, maar weet dat dit mogelijk is door de juiste CNI-plug-in te kiezen (bijvoorbeeld Calico).

# Wat voorbereidingen
We gaan nu één van onze werklasten van een *service* voorzien: `kubectl expose deployment test-deployment1 -n test1 --port=80 --type=NodePort`{{execute}}

Controleer het resultaat en schrijf het IP adres op: `kubectl get service -n test1`{{execute}}

**Schrijf het IP adres van dde service op!**
