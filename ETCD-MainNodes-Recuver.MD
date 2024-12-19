# ETCD Main Recovery Steps

## 1. Remoção dos demais main nodes do arquivo `/etc/etcd.env`

  - Removi os demais main nodes do arquivo: e /etc/etcd.env
    ETCD_INITIAL_CLUSTER=

## 2
  - Removi os demais main nodes do arquivo: 
    manifests/kube-apiserver.yaml

## 3
  - Adicionei as variáveis de ambiente no shell 
    set -a
    source /etc/etcd.env

## 4
  - Adicionei o --force-new-cluster no ExecStart=/usr/bin/etcd

## 5 
 - Check no serviço do etcd.Service

  systemctl daemon-reload
  systemctl restart etcd  
  
  etcdctl member list 
  etcdctl endpoint status

## 6
  Removi o --force-new-cluster no ExecStart=/usr/bin/etcd

  systemctl daemon-reload
  systemctl restart etcd
