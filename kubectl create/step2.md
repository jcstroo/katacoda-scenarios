We hebben nu een deployment, met daarin een replicaset en een POD waar een container in draait. 

# En nu?!
Mooi. Maar wat nu? Hoe kan ik hier iets mee doen? Daar gaan we nu naar kijken. Eerst even wat achtergronden.

## Namespaces
Deployment zijn gekoppeld aan een namespace. We hebben echter geen namespace opgegeven. In dat geval komt het deployment terecht in de *default* namespace. Dit kan je ook terugzien als je je deployment nader bekijkt: `kubectl describe deployment test-deployment | grep Namespace`{{execute}}

Kubernetes maakt standaard een paar eigen namespaces aan voor eigen gebruik en verder zijn er namespace voor gebruikers. kijk maar: `kubectl get namespace`{{execute}} Hoe je die maakt, gaan we later bekijken. We gebruiken nu dus de default namespace van Kubernetes.

## Logging van de container
De container in de POD genereert logging. Alls wat naar std-out wordt geschreven kan kubernetes uitlezen. Probeer maar voor je eigen container door eerst de naam van je pod terug te zoeken: `kubectl get pod`{{execute}} en daarna dit commando te kopieren en daar de naam van je pod achter te voegen: `kubectl logs`{{copy}}. bijvoorbeeld *kubectl logstest-deployment-68f747d97-dnqnk*.

Er staat als het goed is één regel in de log en die is interessant: kennelijk draait er een webserver op poort 80!

## Interactie met de webbserver
De container draait een webserver op poort 80. Maar hier kunnen we nog niet bij komen. De poort is namelijk niet *exposed* naar buiten toe en alleen in het interne netwerk van de namespace beschikbaar.

Daarom gaan we de poort 80 in de container beschikbaar stellen op een willekeurige poort aan de buitenkant via een *NodePort Service*: `kubectl expose deployment test-deployment --port=80 --type=NodePort`{{execute}}

Je krijgt nu de melding *service/test-deployment exposed*. Dat is mooi, maar om te vinden hoe je de service kan bereiken moeten we het externe poort nummer vinden. Dat doe je zo: `kubectl get service`{{execute}}

De output laat alle services zien, waaronder onze service die bij de test-deployment hoort. Hier zie je onder *Port(s)* de mapping van poort 80 naar een poort in de 30000 reeks. Deze poort heb je nodig!

Open browser naar de port door het plusje naast de terminal in katacoda te gebruiken. Kies *Select port to view on host 1* en vul hier het poort nummer in. Je krijgt dan antwoord van de webserver in je pod, bijvoorbeeld: "This request was processed by host: test-deployment-68f747d97-dnqnk"