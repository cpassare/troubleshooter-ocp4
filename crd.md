# CRDs per namespace

```
oc get crd  -o template --template='{{range .items }}{{if eq .spec.scope "Namespaced"}}{{if ne .spec.names.singular "image"}}{{.spec.names.singular}}{{println}}{{end}}{{end}}{{end}}' |  xargs -n 1 oc get --show-kind --ignore-not-found -n openshift-ingress-operator   2>/dev/null
```