# ETCD Main Recovery Steps

## 1. Remoção dos demais main nodes do arquivo `/etc/etcd.env`
    ETCD_INITIAL_CLUSTER=

## 2 Removi os demais main nodes do arquivo: 
    manifests/kube-apiserver.yaml

## 3 Adicionei as variáveis de ambiente no shell
```bash
    set -a
    source /etc/etcd.env
```
## 4 Adicionar config no systemd do etcd:
  --force-new-cluster em ExecStart=/usr/bin/etcd

## 5 Start e  Check no serviço do etcd.Service:
```bash 
  systemctl daemon-reload && systemctl restart etcd 
  etcdctl member list 
  etcdctl endpoint status
````
## 6 Remover config no systemd do etcd:
  Removi o --force-new-cluster no ExecStart=/usr/bin/etcd
  systemctl daemon-reload && systemctl restart etcd
