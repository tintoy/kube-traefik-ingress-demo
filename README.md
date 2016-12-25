# Demo - Traefik Ingress for Kubenetes

A quick demonstration of using Traefik for Ingress on Kubernetes (assumes [kube-solo](https://github.com/TheNewNormal/kube-solo-osx), but if using [kmachine](https://github.com/skippbox/kmachine) just replace `ksolo` with `kmachine`).

1. Generate a hosts file entry for `traefik-ui.local` and `nginx.local`:  
```bash
echo "$(ksolo ip) traefik-ui.local nginx.local" | sudo tee -a /etc/hosts
```
2. Create the Ingress Controller:  
```bash
kubectl apply -f traefik-ingress.yml
```
3. Expose the Traefik UI:  
```bash
kubectl apply -f traefik-ui.yml
```
4. Open your browser and navigate to [http://traefik-ui.local/](http://traefik-ui.local/) (verify that the Traefik UI comes up).
5. Create the NGINX Deployment, Service, and Ingress:  
```bash
kubectl apply -f nginx.yml
```
6. Open your browser and navigate to [http:/nginx.local/](http:/nginx.local/).
