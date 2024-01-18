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


"""" This is one way
helm upgrade --install prometheus prometheus-community/kube-prometheus-stack --wait
kubectl --namespace default get pods -l "release=prometheus"
kubectl get pods --all-namespaces 

""""

The easy way to make node use kubectl to work is to copy the config from "master node" usually found here : /etc/kubernetes/admin.conf , to whetever node you want to configure kubectl ( even on master node) . The location to be copied is : $HOME/.kube/config.

Use scp prometheus@192.168.1.10:.kube/config prometheus@192.168.1.11:.kube/ (this command will copy the config file from master to node and make node works of kubectl) let suppose ip 192.168.1.10 is master.

kubectl create namespace prometheus (run this command to create prometheus namespace for prometheus)



