# setup k8s cluster's with Ansible and kubeadm

## using

```shell
$ ansible-playbook site.yaml \
--inventory.yaml=inventories/hosts \
--private-key /home/xxxx/ssh-key-ansible-sa \
--user xxxx \
--diff \
-v 
```


## refs

- [GCPで基本に戻って始める実践 Infrastructure as code再入門#2 | VISASQ TECH BLOG](https://tech.visasq.com/restart-gcp-infrastructure-as-code2/)
- [ansible/workshops: Training Course for Ansible Automation Platform](https://github.com/ansible/workshops)
- [Self-managed Kubernetes in Google Compute Engine (GCE)](https://projectcalico.docs.tigera.io/getting-started/kubernetes/self-managed-public-cloud/gce)
- [workshops/README.ja.md at devel · ansible/workshops](https://github.com/ansible/workshops/blob/devel/exercises/ansible_rhel/1.3-playbook/README.ja.md)
- [Deploy a Kubernetes Cluster using Ansible - buildVirtual](https://buildvirtual.net/deploy-a-kubernetes-cluster-using-ansible/)
- [GCPで基本に戻って始める実践 Infrastructure as code再入門#2 | VISASQ TECH BLOG](https://tech.visasq.com/restart-gcp-infrastructure-as-code2/)
- [ansible/workshops: Training Course for Ansible Automation Platform](https://github.com/ansible/workshops)
- [Kubernetesクラスタ構築を例に既存の作業をAnsible化するポイント / initialize kubeadm by ansible - Speaker Deck](https://speakerdeck.com/zaki_lknr/initialize-kubeadm-by-ansible)
- [zaki-lknr/initialize-kubeadm-ansible: kubeadmでk8sクラスタデプロイするAnsible Playbook](https://github.com/zaki-lknr/initialize-kubeadm-ansible)
- [[Kubernetes] kubeadmを使ってCentOSへk8sクラスタをデプロイしてみた (firewalld有効版) - zaki work log](https://zaki-hmkc.hatenablog.com/entry/2020/03/19/191534)
- [kubeadmを使用したクラスターの作成 | Kubernetes](https://kubernetes.io/ja/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/)
- [k8s on RaspberryPiでHAクラスタ構築](https://zenn.dev/nkte8/articles/2021-09-26-r01)
- [我が家のおうちKubernetesの成長記録 | IIJ Engineers Blog](https://eng-blog.iij.ad.jp/archives/11900)