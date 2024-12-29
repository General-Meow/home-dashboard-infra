steps created for this setup
1. download the install file from the documentation, https://argo-cd.readthedocs.io/en/stable/getting_started/ here: https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
2. customise argocd by providing configmap properties in "argocd-cmd-params-cm" so that it runs in unsecure mode. server.insecure: "true"  
3. customise argocd by providing configmap properties in "argocd-cmd-params-cm" so that it runs on a different root path for the ingress.   server.rootpath: "/argocd"  (don't know why, but doing things using the middleware to strip the path doesn't seem to work, so we do it this way)

to install
1. run `brew install argocd`
2. run `kubectl create namespace argocd`
2. run `k apply -n argocd -f argo-install.yaml`
2. run `k apply -f ingress-argocd.yaml`
3. navigate to `localhost/argocd`
4. run `argocd admin initial-password -n argocd`
5. goto `http://localhost/argocd`
5. login using the `admin` user and the generated password
6. The page refreshes weired and puts an extra `/argocd` in the url. just remove it and it will work e.g. goto `http://localhost/argocd/applications` 