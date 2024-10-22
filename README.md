# helloworld-test

OC client installation:
https://docs.openshift.com/container-platform/4.8/cli_reference/openshift_cli/getting-started-cli.html

Openshift: <br>
Aufgaben: <br>
User Hinzufügen: <br>
oc get secret htpass-secret -ojsonpath={.data.htpasswd} -n openshift-config | base64 --decode > users.htpasswd <br>
<br>
htpasswd -bB users.htpasswd <username> <password> <br>
<br>
oc create secret generic htpass-secret --from-file=htpasswd=users.htpasswd --dry-run=client -o yaml -n openshift-config | oc replace -f - <br>
<br>
Rechte (Cluster Admin): <br>
oc adm policy add-cluster-role-to-user cluster-admin <user> <br>
Namespace anlegen <br>
<br>
<br>
ArgoCD <br>

Git Project in eigenes Clonen (https://github.com/tobias-viada/helloworld-test.git ) Und das eigene GitProject im ArgoCD als Repo anlegen <br>
Namespace Rolebindings ändern. <br>
(rolebindings.yaml anlegen. Inhalt hinzufügen:
"apiVersion: v1
kind: Namespace
metadata:
  name: <Namespace Name>
  labels:
    argocd.argoproj.io/managed-by: argocd"
<br>
Im ArgoCD das neue Git Projekt hinzufügen
In den angelegten Namespace deployen
<br>
Im Git die „welcome_message“ in der configmap.yaml ändern und neu Syncen
<br>
<br>
neues Repo anlegen: https://github.com/argoproj/argocd-example-apps
"kustomize-guestbook" deployen und den Fehler finden

