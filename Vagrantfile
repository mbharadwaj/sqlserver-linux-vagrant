# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  # Open SQL Server port to host
  config.vm.network "forwarded_port", guest: 1433, host: 1433

  config.vm.provider "virtualbox" do |vb|
    # SQL server needs 3.25G
    vb.memory = "4096"
  end

  # WARNING: SA_PASSWORD is in plain text
  config.vm.provision "shell", env: {"SA_PASSWORD" => "Password123", "ACCEPT_EULA" => "Y"}, inline: <<-SHELL
    curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
    curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list > /etc/apt/sources.list.d/mssql-server.list
    curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/msprod.list
    apt-get update

    apt-get install -y mssql-server
    /opt/mssql/bin/sqlservr-setup --accept-eula --set-sa-password --enable-service --start-service

    apt-get install -y mssql-tools
  SHELL
end
