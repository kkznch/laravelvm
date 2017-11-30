# coding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # 使用するboxファイル
    config.vm.box = "bento/centos-7"

    # ゲストOSのメモリサイズとCPUコア数
    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", 4096, "--cpus", 2, "--ioapic", "on"]
    end

    # ゲストOSのホスト名とプライベートIP
    config.vm.define "laravelvm" do |lvm|
        lvm.vm.network "private_network", ip: "192.168.16.132"
    end

    # 共有フォルダの設定
    config.vm.synced_folder "./shared/", "/var/www", mount_options: ['dmode=777','fmode=777'], create: true

    # ゲストOS毎に異なる公開鍵を使用しない
    config.ssh.insert_key = false

    # ansibleを使ったプロビジョニング
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook/provisioning/setup.yaml"
        ansible.inventory_path = "playbook/inventory/hosts"
        ansible.limit = 'all'
    end
end
