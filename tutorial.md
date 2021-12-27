
# 1. Ansibleを、Ansible実行用のインスタンスにインストールする

```shell
# 何もせずにaptでそのままインストールすると古いAnsibleがインストールされ、本playbookが動かない場合があるので注意。
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

```shell
# インストールしようとするバージョンをチェックしてから、apt installを実行すると良い
$ apt show version ansible
```

```shell
# インストール後、versionを確認しておく
$ ansible --version
ansible 2.9.27
```

refs
- [ansible/workshops: Training Course for Ansible Automation Platform](https://github.com/ansible/workshops)
- [Ansible のインストール — Ansible Documentation](https://docs.ansible.com/ansible/2.9_ja/installation_guide/intro_installation.html)


# 2. Ansibleからpingをlocalにむけて実行してみる

localhostにむけて Ansibleでpingを実行してみる。(inventoryファイルを作らずに直接実行)

```shell
# localにむけてping
$ ansible -i 127.0.0.1, all \
  -m ping \
  --connection=local

# responseが帰ってくる。ping -> pongがかえってくれば成功。

127.0.0.1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}
```

このとき、ansibleを動かすためのpythonのバージョンが2系になってるのでwarningがでることがある。。後述のplaybookではちゃんとバージョンを指定する。

```shell
[DEPRECATION WARNING]: Distribution Ubuntu 18.04 on host controller should use 
/usr/bin/python3, but is using /usr/bin/python for backward compatibility with prior Ansible
 releases. A future Ansible release will default to using the discovered platform python for
 this host. See 
https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for 
more information. This feature will be removed in version 2.12. Deprecation warnings can be 
disabled by setting deprecation_warnings=False in ansible.cfg.
```


# 3. Ansibleからpingを他ホストにむけて実行してみる

他インスタンスに向けてpingを打ってみる

```shell
# 他のVMにむけてping
$ ansible -i `target_hostname`, all -m ping
```

つながらない場合は、sshの設定や公開鍵配布、ユーザ作成などをしてから、再度実行してみる。

```shell
$ ansible \
-i controller, all \
-m ping \
--private-key /home/xxxxxx/ssh-key-ansible-sa \
--user xxxxxx \
--diff \
-v
```

# 4. playbookを書いて実行。

ansible-playbookを実行できるか試す。

```shell
$ ansible-playbook site.yaml \
--inventory.yaml=inventories/hosts \
--private-key /home/xxxx/ssh-key-ansible-sa \
--user xxxx \
--diff \
-v 
```
