# k8s-prometheus

#Install helm by going to
#helm.sh/docs/intro/install

#Install by script
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
$ chmod 700 get_helm.sh
$ ./get_helm.sh
# at successful installation it will be print "helm installed into /usr/local/bin/helm"

helm repo update
helm search repo prometheus
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

helm upgrade --install prometheus prometheus-community/kube-prometheus-stack --wait
kubectl --namespace default get pods -l "release=prometheus"
kubectl get pods --all-namespaces
