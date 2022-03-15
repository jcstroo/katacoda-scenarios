# Kennismaken met Katacoda
De testomgeving is nu beschikbaar! Maar nog niet helemaal... Op de achtergrond bouwt het systeem nog een paar zaken op, dus niet te snel starten, heb even geduld en doorloop deze eerste kennismaking!

## Katacoda
In deze testomgeving kan en commando's typen in de shell (onderaan) en je kan file bekijken via de file explorer (bovenaan)

Tik maar eens een commando in, bijvoorbeeld "ls -la".

Katacoda maakt het invoeren van commando's makkelijk voor je. Probeer nu dit commando nogmaals via het execute knopje achter het commando: `ls -la`{{execute}}

De hele cursus is op deze manier gemaakt: een beetje uitleg en dan wat commando's om uit te voeren. Simpel!

Je mag ook gerust andere commando's intikken. Dat is geen probleem. Maar hou je wel aan de volgorde van de opdrachten, anders loop je halverwege vast!

En om het echt goed te leren raden we het aan om de commando's zelf in te typen. Als je alleen op de execute logo's klikt mis je toch een beetje dat echte gevoel van werken op de terminal :)

## Kunnen we al verder?
Hopelijk is het systeem nu echt klaar! Voer onderstaande instructie uit om dit te controleren. En nee, deze hoef je niet over te typen :)

`while [ ! -f /root/.kube/config ]; do sleep 5 && echo "nog even geduld..."; done && echo "We kunnen verder!"`{{execute}}

Zodra "We kunnen verder!" in beeld komt, kan je door naar de volgende stap!