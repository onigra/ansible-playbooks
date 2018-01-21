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

- https://github.com/geerlingguy/ansible-role-mysql/pull/243

# usage

- `.secrets` 配下にansible vaultで暗号化したファイルが置いてある想定になっている
  - 環境ごとのファイルが置いてあり、 `--extra-vars` で `secret_env` という変数名からファイル名を指定する想定
  - 例えば `.secrets/dev.yml` がある場合、 `--extra-vars "secret_env=dev"` となる

```sh
vagran up
source ./py3-ansible/bin/activate
ansible-playbook -i inventory/dev.yml site.yml --extra-vars "secret_env=dev"
```

