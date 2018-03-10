# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define :web do |web|
    web.vm.box = "ubuntu/xenial64"
    web.vm.hostname = "web"
    web.vm.network :forwarded_port, guest: 80, host: 8080
    web.vm.network :private_network, ip: "192.168.33.10"
  end

  config.vm.define :db do |db|
    db.vm.box = "ubuntu/xenial64"
    db.vm.hostname = "db"
    db.vm.network :forwarded_port, guest: 3306, host: 13306
    db.vm.network :private_network, ip: "192.168.33.11"
  end

  config.vm.define :redis do |redis|
    redis.vm.box = "ubuntu/xenial64"
    redis.vm.hostname = "redis"
    redis.vm.network :forwarded_port, guest: 6379, host: 16379
    redis.vm.network :private_network, ip: "192.168.33.12"
  end

end

