# k8s-ingress-with-kind-port-mapping
Access to the k8s app through the nginx ingress controller, which is hosted on a kind cluster.
# Access your kubernetes app from host machine

Created time: January 13, 2026 8:47 PM

Diagram.

Story

### Step1:

Map the NodePort in your Kind Config [Creating kind cluster with port mapping](https://www.notion.so/Creating-kind-cluster-with-port-mapping-2e71b1e58fc080648e1bdaf0c2ac8479?pvs=21) 

### Step:2

Create a kind cluster with configured kind-config.

### Step:3

Apply Nginx Ingress Controller on the Cluster.

[NGINX Ingress Controller](https://www.notion.so/NGINX-Ingress-Controller-1fe1b1e58fc080dd92e2d9c0559100a4?pvs=21) 

Step:4

Change the NodePort from Nginx Ingress Controller Service.

1. Get the Service name `kubectl get svc -n ingress-nginx`
    
    ```powershell
    vagrant@hellocloud-native-box:~/svs-microservices-testing/svs-microservices/k8s$ kubectl get svc -n ingress-nginx
    NAME                                 TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
    ingress-nginx-controller             NodePort    10.127.174.38    <none>        80:30322/TCP,443:32013/TCP   48m
    ingress-nginx-controller-admission   ClusterIP   10.127.194.206   <none>        443/TCP                      48m
    ```
    
2. Edit the NodePort to match with configured NodePort at kind-config.yaml
    1. `kubectl edit svc ingress-nginx-controller -n ingress-controller`
        
        
3. Verify the updated NodePort `kubectl get svc -n ingress-nginx`
4. Install [NGINX Ingress Controller](https://www.notion.so/NGINX-Ingress-Controller-1fe1b1e58fc080dd92e2d9c0559100a4?pvs=21) 
5. Deploy  ([svs-microservices](https://github.com/kyawzinmyolwin/svs-microservices/tree/ec810c00d262ca763a5bad2dc23e84f61b9285df/k8s))