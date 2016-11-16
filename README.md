# Vagrantfile for SQL Server Linux

* Runs on Ubuntu
* Sets SA_PASSWORD to a default
* Installs server and client tools
* Accepts EULA

# WARNING

Please update SA_PASSWORD

# Start/Stop/Verify server up/down
    systemctl status mssql-server
    sudo systemctl start mssql-server
    sudo systemctl stop mssql-server

# SQL Server client
    sqlcmd -S localhost -U SA -P '<Password>'
