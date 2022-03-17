
# werklasten in de namespaces
We hebben net twee nieuwe namespaces gemaakt. Laten we nu wat werklasten in deze namespaces starten. Dit kan met het *kubectl create* commando door er expliciet een namespace bij te vermelden:
`kubectl create deployment test-deployment1 -n test1 --image=katacoda/docker-http-server`{{execute}}
`kubectl create deployment test-deployment2 -n test1 --image=katacoda/docker-http-server`{{execute}}
`kubectl create deployment test-deployment3 -n test1 --image=katacoda/docker-http-server`{{execute}}

`kubectl create deployment test-deployment4 -n test2 --image=katacoda/docker-http-server`{{execute}}
`kubectl create deployment test-deployment5 -n test2 --image=katacoda/docker-http-server`{{execute}}
`kubectl create deployment test-deployment6 -n test2 --image=katacoda/docker-http-server`{{execute}}

Kijk nu naar de werklasten: `kubectl get pod`{{execute}}

Waarom zie je nu niets?? Dat komt omdat je normaal alleen de werklasten in de *default* namespace ziet! We hebben de werklasten nu niet in de default namespace geplaatst, maar in twee eigen namespaces. Probeer onderstaande commando's maar eens:

Om alle PODs in de namespace test1 te zien: `kubectl get pod -n test1`{{execute}}
Om alle PODs in de namespace test1 te zien: `kubectl get pod -n test2`{{execute}}
Om alle PODs in alle namespaces te zien: `kubectl get pod -A`{{execute}} of `kubectl get pod --all-namespaces`{{execute}}

Bovenstaande geldt voor alle commando's, dus ook voor deployment, services, etc... Hier ga je vast nog wel een keer tegen aan lopen...
