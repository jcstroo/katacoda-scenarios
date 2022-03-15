De test omgeving is nu beschikbaar! Op de achtergrond bouwt het systeem nog een paar zaken op, dus niet te snel starten, heb even geduld.

In deze testomgeving kan en commando's typen in de shell (onderaan) en je kan file bekijken via de file explorer (bovenaan)

Tik maar eens een commando in, bijvoorbeeld "ls -la".

Katacoda maakt het invoeren van commando's makkelijk voor je. Probeer nu dit commando nogmaals via het execute knopje achter het commando: `ls -la`{{execute}}

Dat was om even op te warmen. Inmiddels zal de omgeving wel helemaal opgebowud zijn. Laten we dit controleren.

1) als het goed is zit je in de directory van de user "root"
`pwd`{{execute}}

2) zo niet, ga hier dan alsnog naar toe:
`cd /root`{{execute}}

3) bekijk nu de files en folders in deze directory:
`ls -la`{{execute}}

4) je ziet een directory met de naam ".kube". Ga hier naar toe:
`cd .kube`{{execute}}

5) In de directory .kube staat meerdere files, waaronder een file genaamd "config"
`ls -la`{{execute}}

6) Lees deze file nu:
`more config`{{execute}}
