# Kubeconfig 
Dat was om even op te warmen en om het systeem de tijd te geven om wat zaken klaar te zetten. Inmiddels zal de omgeving wel helemaal opgebouwd zijn. Laten we dit controleren.

1. als het goed is zit je in de home directory van de user "root" (/root). Controleer dit aub!
`pwd`{{execute}}

2. Als je in een andere directory zit: ga dan aub terug naar /root:
`cd /root`{{execute}}

3. bekijk nu de files en folders in deze directory:
`ls -la`{{execute}}

4. je ziet een directory met de naam ".kube". Directories met een punt aan het begin zijn hidden directories in linux. Ga hier naar toe:
`cd .kube`{{execute}}

5. In de directory .kube staat meerdere files, waaronder een file genaamd "config"
`ls -la`{{execute}}

6. Lees deze file nu. Let er op dat je in katacoda even moet scrollen in de terminal.
`cat config`{{execute}}

Dit is de kubeconfig file. Deze is deels leesbaar, maar er staat ook een heleboel onleesbare tekst in. Dat is bewust: dat zijn de sleutels die je toegang geven tot het kubernetes cluster!

Deze file is dus belangrijk en moet je veilig bewaren, want met deze file krijg je toegang tot het cluster.

De file heeft twee delen:
1. clusters: dit is de sleutel van het cluster en geeft het API-adres van het cluster aan
2. contexts: dit geeft aan hoe en met welke user je verbinding maakt met het cluster. Wederom op basis van een certificaat.

je kan de file in katacoda ook in de verkenner bekijken boven in beeld of direct openen via deze optie:
`.kube/config`{{open}}