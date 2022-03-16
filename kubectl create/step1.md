
# Deployments
Voor deze oefening gebruik je een nieuwe machines. Wacht totdat deze helemaal klaar is door dit commando te geven:
`while [ ! -f /root/.kube/config ]; do sleep 5 && echo "nog even geduld..."; done && echo "We kunnen verder!"`{{execute}}

## Je eerste deployment op de commandline
We gaan een eenvoudig deployment maken met één container in een Pod. Deze container is een webserver die je in één commando kan starten. We gebruiken hiervoor *kubectl create deployment*. Hierbij geef je je deployment een naam (test-deployment) en geef je aan welke container gestart moet worden (katacoda/docker-http-server).

`kubectl create deployment test-deployment --image=katacoda/docker-http-server`{{execute}}

Je krijgt nu de melding: *deployment.apps/test-deployment created*!

Je kan zien dat het gelukt is doot het volgende commando te geven: `kubectl get deployment`{{execute}}. Maar nu weet je nog niet zo veel. Dus kan je meer details vragen met het commando: `kubectl describe deployment test-deployment`{{execute}}

## Een replicaset?!
Je kan in de output van het vorige commando een zogenaamde "ReplicaSet" terugvinden. Die is kennelijk automatisch aangemaakt. 
De naam van de replicaset zie je ook terug met het volgende commando: `kubectl get replicaset`{{execute}}.

Net als eerder kan je ook meer details van de replicaset opvragen. Kopieer het commando uit dit veld: `kubectl describe replicaset`{{copy}} en vul hier achter de naam van de replicaset in. Bijvoorbeeld: *kubectl describe replicaset test-deployment-68f747d97*.

Je kan nu zien hoeveel replica's er verwacht worden onder de *annotations* en bij *Replica's*. En hier vinden we helemaal onderaan de naam van de POD. Die hebben we nu nodig!

## De POD
Bij het maken van de deployment is een replicaset gemaakt (met één replica) én vanuit de replicaset is een POD gemaakt, waar de contianer in draait. Kijk maar naar de PODs: `kubectl get pod`{{execute}}.  

Ook nu kan je weer aanvullende informatie opvragen met *kubectl describe*. kopieer het volgende commando en plak het in de terminal. Vul het aan met de naam de pod: `kubectl describe pod`{{copy}}
