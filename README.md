install k3s 
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION="v1.24.8-rc1+k3s1" INSTALL_K3S_EXEC="server --no-deploy traefik" K3S_KUBECONFIG_MODE="644" sh -s - server --cluster-init

cp /etc/rancher/k3s/k3s.yaml ~/.kube/config

https://docs.ranchermanager.rancher.io/v2.6/getting-started/quick-start-guides/deploy-rancher-manager/helm-cli

se precisar forcar o ip externo
kubectl patch svc ingress-nginx-controller -n ingress-nginx -p '{"spec": {"type": "LoadBalancer", "externalIPs":["192.168.65.60"]}}'

registre 

crie o arquivo sudo nano /etc/rancher/k3s/registries.yaml e restart o serviço "service k3s restart"

1
mirrors:
2
  docker.io:
3
    endpoint:
4
      - "https://rud.desenvolvimento.redeunifique.com.br"
5
configs:
6
  "rud.desenvolvimento.redeunifique.com.br":
7
    auth:
8
      username: rud
9
      password: ****
10
    tls:
11
      insecure_skip_verify: true
12
      #cert_file: # path to the cert file used in the registry
13
      #key_file:  # path to the key file used in the registry
14
      #ca_file:   # path to the ca file used in the registry
Se após reboot ou instalar o rancher não subir tem que desativar o firewalld 
desistalar 

/usr/local/bin/k3s-uninstall.sh

https://docs.redeunifique.com.br/link/667#bkmrk-rm--f-%2Fusr%2Flocal%2Fbin
 
rm -f /usr/local/bin/k3s
