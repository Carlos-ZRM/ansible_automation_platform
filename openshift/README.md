# Generate sa

oc create sa ansible-sa -n default
oc adm policy add-cluster-role-to-user cluster-admin -z ansible-sa -n default
export TOKEN=$(oc create token -n default  ansible-sa  --duration=8760h)

# Generate kubeconfig file


oc login --server=https://api.h1v8e7jh.eastus.aroapp.io:6443 --token=$TOKEN --kubeconfig=./sa-kubeconfig

oc get pods -n openshift-etcd  -l app=etcd --field-selector=status.phase==Running -o name