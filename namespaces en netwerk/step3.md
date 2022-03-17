
# Het netwerk in een namespace
binnen kubernetes wordt op basis van een CNI-plug-in een virtueel (overlay) netwerk gemaakt. Dit werkt zelfs over nodes heen. Dus ook in een cluster met meerdere nodes heb een virtueel netwerk. Hier hoef je niets voor te doen.

Geef het volgende commando om meer informatie over je pods te zien: `kubectl get pod -n test1 -o wide`{{execute}}
Doe hetzelfde voor de andere namespace: `kubectl get pod -n test2 -o wide`{{execute}}

**Schrijf het IP adres van de eerste pod die hoort bij deployment test-deployment1 op!**

Je ziet dat de pods allemaal een (opvolgend) IP adres hebben gekregen. Dat is de default werking van kubernetes: het virtuele netwerk werkt over alle namespace heen. Je kan dit ook aanpassen, met netwerk isolatie per namespace. Dat is voor nu buiten scope van deze training, maar weet dat dit mogelijk is door de juiste CNI-plug-in te kiezen (bijvoorbeeld Calico).

# Wat voorbereidingen
We gaan nu één van onze werklasten van een *service* voorzien: `kubectl expose deployment test-deployment1 -n test1 --port=80 --type=NodePort`{{execute}}

Controleer het resultaat en schrijf het IP adres op: `kubectl get service -n test1`{{execute}}

We starten nu een extra container in de eerste namespace met wat netwerk tools: `kubectl create deployment multitool -n test1 --image=praqma/network-multitool`{{execute}}

Hierna gaan we verbinding maken met de bash-shell van de container. Dat kan pas zodra deze opgestart is. 
- Controleer met `kubectl get pod -n test1 -o wide`{{execute}} of de container de status "running" heeft. Dit kan even duren.
- schrijf het ip-adres van de container op. Die zie je ook pas als de continer running is!
- Zodra deze running is, kan je er mee verbinden: `kubectl exec -it -n test1 <pod naam> /bin/bash`{{copy}}

## Netwerk tools
We zitten nu in de container. Hier gaan we wat eenvoudige netwerk controles doen:
- Vraag hiet het IP-adres van de container op: `ip addr show`{{execute}} Klopt dit met wat je eerder had gevonden?
- Ping nu één van de andere pods die je eerder heb opgevraagd op basis van het interne cluster ip adres met het *ping* commando: `ping -c4 <ip adres>`{{copy}}

Er is ook een DNS-service actief binnen het cluster. In /etc/resolv.conf worden namelijk wat aanpassingen gedaan. Je ziet hier een IP adres van een nameserver en een aantal netwerk suffixen: `cat /etc/resolv.conf`{{execute}}

We gaan nu op basis van DNS wat zaken bekijken:
- de POD staat in de interne DNS met een cryptische naam op basis van het ip adres, de namespace en het type (pod), bijvoorbeeld: 172-17-0-3.default.pod
- Een service is wat makkelijker en kan benaderd worden op de naam van de service en de namespace: test-deployment1.test1

We gaan met nslookup de service en pod opzoeken:
- start nslookup: `nslookup`{{execute}}
- vraag eerst de pod op door het IP adres te gebruiken en de punten te vervangen door streepjes (hyphens), gevolgd door de naam van de namespace en het type "pod", bijvoorbeeld: **10-32-0-5.test1.pod**
- Vraag nu de service op door de naam van het deployment te gebruiken, gevolgd door de naam van de namespace: `test-deployment1.test1`{{execute}}




