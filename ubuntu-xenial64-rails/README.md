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

# Usage

- `.secrets` 配下にansible vaultで暗号化したファイルが置いてある想定になっている
  - 環境ごとのファイルが置いてあり、 `--extra-vars` で `secret_env` という変数名からファイル名を指定する想定
  - 例えば `.secrets/dev.yml` がある場合、 `--extra-vars "secret_env=dev"` となる

## All in one

1つのホストに全部入り

- setup vagrant

```sh
ln -s vagrant_files/all_in_one.rb
vagrant up
```

- execute playbook

```sh
ansible-playbook -i inventory/all_in_one.yml playbooks/all_in_one.yml --extra-vars "secret_env=all_in_one"
```

## Split

web, db, redsでロールが分かれている

- setup vagrant

```sh
ln -s vagrant_files/split.rb
vagrant up
```

- execute playbook

```sh
ansible-playbook -i inventory/split.yml playbooks/split.yml --extra-vars "secret_env=split"
```

