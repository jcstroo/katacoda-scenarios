
# Tijd om op te ruimen
Je deployment werkt! we hebben een werkende webserver opgeleverd en we gaan dit nu weer opruimen. 

- verwijder eerst het deployment: `kubectl delete deployment test-deployment`{{execute}}
- kijk nu of het deployment inderdaad weg is: `kubectl get deployment`{{execute}}
- kijk nu of hde replicaset weg is: `kubectl get replicaset`{{execute}}. Als het goed is, is die nu ook weg.
- kijk nu of de Pod ook weg is: `kubectl get pod`{{execute}}. Als het goed is, is die nu ook weg.

## De service opruimen
Kubernetes ruimt zijn rommel dus best netjes op. Alles wat met het kubctl create commando is aangemaakt, wordt ook weer netjes verwijderd. En de Service? Die niet, kijk maar: `kubectl get svc`{{execute}}. Deze is immers op een andere manier aangemaakt en staat los van het deployment. Gooi deze daarom met de hand weg: `kubectl delete svc test-deployment`{{execute}}.
