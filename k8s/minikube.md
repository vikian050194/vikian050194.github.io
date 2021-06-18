## minikube

Recently I took part in an intensive course "k8s for developers" made by slurm.io and it was awesome. Before it I had only passive knowledge in this area, only once tried to connect to pod via kubectl, but the general idea in first approximation was almost clear. After it I have quite a good understanding of what's going on and a lot of practice experience. That’s great!

Right now I intend to dig a bit deeper and find a few more answers for questions related to k8s and minikube in particular.

### k8s

1. What is **RBAC**?
2. **Role** and **ClusterRole**?
3. **RoleBindings** and **ClusterRoleBinding**?
4. **ServiceAccount**?
5. Manifest that contains `kind: Ingress` is a instruction for Ingress controller?
6. What is Service? ClucterIP, NodePort, LoadBalancer, ExternalName and ExternalIPs?

   Service is k8s abstraction related to network.
7. How to install and configure **nginx ingress controller** from scratch?
8. How to install and configure **traefik ingress controller** from scratch?
9. How to install and configure **dashboard** from scratch?
10. Has **nginx ingress controller** admin UI?
11. Does **traefik ingress controller** work only via **RBAC**?
12. How to use latest version of **traefik ingress controller**?

### minikube

1. What is **ingress** addon?
   ```bash
    nginx(docker) > minikube addons enable ingress
    ▪ Using image k8s.gcr.io/ingress-nginx/controller:v0.44.0
    ▪ Using image docker.io/jettech/kube-webhook-certgen:v1.5.1
    ▪ Using image docker.io/jettech/kube-webhook-certgen:v1.5.1
    ```
2. What is **ingress-dns** addon?
3. Does **nginx ingress controller** pre-installed or pre-configured?
4. Why RAM and CPU limits are not applicable?

   It's impossible to set limits if none-driver is in use: minikube uses all available resources.

   If you use any driver apart from none-driver then just recreate minikube to use required limits:
   ```bash
   minikube stop
   minikube delete
   minikube start --vm-driver=<driver name> --cpus 4 --memory 8192
   ```
5. ???

### microk8s

1. Pros and cons?

### k3s

1. Pros and cons?
