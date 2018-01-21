# Vagrant ubuntu image

- https://app.vagrantup.com/ubuntu/boxes/xenial64

# galaxy install

```sh
ansible-galaxy install -p ./galaxy -r requirements.yml
```

# py3-ansible

- xenial64にはpython3が入ってるので、ansibleのpython3版を使う必要がある

```sh
sudo easy_install virtualenv
virtualenv py3-ansible
source ./py3-ansible/bin/activate
```

# playbook実行時に出るDEPRECATION WARNINGはgalaxyのplaybookのせい

- https://github.com/zzet/ansible-rbenv-role

```
[DEPRECATION WARNING]: The use of 'include' for tasks has been deprecated. Use 'import_tasks' for static inclusions or 'include_tasks' for dynamic inclusions. This feature will be removed in a future release. Deprecation warnings can be
disabled by setting deprecation_warnings=False in ansible.cfg.
[DEPRECATION WARNING]: include is kept for backwards compatibility but usage is discouraged. The module documentation details page may explain more about this rationale.. This feature will be removed in a future release. Deprecation
warnings can be disabled by setting deprecation_warnings=False in ansible.cfg
```

# usage

```sh
vagrant up
source ./py3-ansible/bin/activate
ansible-playbook -i inventory/dev.yml site.yml
```
