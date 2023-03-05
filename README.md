rancher k3s

install k3s
```
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION="v1.24.8-rc1+k3s1" INSTALL_K3S_EXEC="server --no-deploy traefik" K3S_KUBECONFIG_MODE="644" sh -s - server --cluster-init
```
adicionar kubectl local
```
cp /etc/rancher/k3s/k3s.yaml ~/.kube/config
```
https://docs.ranchermanager.rancher.io/v2.6/getting-started/quick-start-guides/deploy-rancher-manager/helm-cli

se precisar forcar o ip externo
```
kubectl patch svc ingress-nginx-controller -n ingress-nginx -p '{"spec": {"type": "LoadBalancer", "externalIPs":["192.168.65.60"]}}'
```
registre

crie o arquivo sudo nano /etc/rancher/k3s/registries.yaml e restart o serviço "service k3s restart"

```
mirrors:
  docker.io:
    endpoint:
      - "https://registry_privado_url"
configs:
  "registry_privado_url":
    auth:
      username: rud
      password: ****
    tls:
      insecure_skip_verify: true
      #cert_file: # path to the cert file used in the registry
      #key_file:  # path to the key file used in the registry
      #ca_file:   # path to the ca file used in the registry
```

Se após reboot ou instalar o rancher não subir tem que desativar o firewalld

desistalar
```
/usr/local/bin/k3s-uninstall.sh

rm -f /usr/local/bin/k3s
```
