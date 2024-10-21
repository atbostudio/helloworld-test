# helloworld-test

Openshift:
Aufgaben:
User Hinzufügen:
oc get secret htpass-secret -ojsonpath={.data.htpasswd} -n openshift-config | base64 --decode > users.htpasswd

htpasswd -bB users.htpasswd <username> <password>

oc create secret generic htpass-secret --from-file=htpasswd=users.htpasswd --dry-run=client -o yaml -n openshift-config | oc replace -f -

Rechte (Cluster Admin):
oc adm policy add-cluster-role-to-user cluster-admin <user>
Namespace anlegen


ArgoCD

Git Project in eigenes Clonen (https://github.com/tobias-viada/helloworld-test.git ) Und das eigene GitProject im ArgoCD als Repo anlegen
Namespace Rolebindings ändern. 
(rolebindings.yaml anlegen. Inhalt hinzufügen:
"apiVersion: v1
kind: Namespace
metadata:
  name: <Namespace Name>
  labels:
    argocd.argoproj.io/managed-by: argocd"

Im ArgoCD das neue Git Projekt hinzufügen
In den angelegten Namespace deployen

Im Git die „welcome_message“ in der configmap.yaml ändern und neu Syncen


neues Repo anlegen: https://github.com/argoproj/argocd-example-apps
"kustomize-guestbook" deployen und den Fehler finden

