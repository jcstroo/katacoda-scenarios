# kubectl
Als je met kubernetes wilt werken heb je de commandline "kubectl" (kubernetes control) nodig. Deze is al geinstalleerd op ons systeem. 

Met kubectl kan je alles in je kubernetes cluster doen, van controles, tot en met het starten van werklasten en het aanmaken van loadbalancers. Het is echt heel krachtig!


## Tijd voor wat actie!
Laten we eerst eens kijken of kubectl er daadwerkelijk op staat: `kubectl version --client`{{execute}}

Met kubectl kan je zoals gezegd heel veel. Kijk maar eens in de help: `kubectl --help`{{execute}}

We vragen nu eerst informatie op uit de kubeconfig file: `kubectl config get-clusters`{{execute}} 

Je ziet nu één cluster, genaamd "kubernetes". Je kan nu ook opvragen hoe we met dit cluster kunnen verbinden: `kubectl config get-contexts`{{execute}}

We kunnen nu aan het cluster wat meer informatie vragen: `kubectl get nodes`{{execute}} om de nodes in het cluster op te vragen. Je ziet nu maar één node met de naam controlplane. Hier kan je meer informatie over opvragen: `kubectl describe node controlplane`{{execute}} Kan je nu het IP adres van de node vinden?

## kubectl en de kube config file
kubectl praat met je cluster op basis van de gegevens in de kubeconfig file. Als er in file in je home directory staat in .kube/config, dan pakt kubectl deze standaard op. Je kan de locatie ook meegeven met de optie --kubeconfig <pad naar config file> of deze in een environmentvariabele zetten:

`export KUBECONFIG_MY_CLUSTER=/root/.kube/config`{{execute}}

En nu kan je met deze variabele verbinden met het cluster:

`kubectl --kubeconfig $KUBECONFIG_MY_CLUSTER get nodes`{{execute}}


