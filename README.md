# postgres-db

Create the file repository configuration:

    sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

Import the repository signing key:

    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

Update the package lists:

    sudo apt-get update

Install the latest version of PostgreSQL. If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql':
    
    sudo apt-get -y install postgresql

Start the service

    sudo systemctl start  postgresql

Status of postgresql

    sudo systemctl status  postgresql

User password assign

    $ sudo -i
    # su - postgres
    $ psql

        postgres=# \l
        postgres=# \c postgres
        postgres=# ALTER USER postgres WITH PASSWORD '.';
        postgres=# \q
    
    $ exit
    # sudo vim /etc/postgresql/12/main/pg_hba.conf

        # Database administrative login by Unix domain socket
        # Insert the line
        # TYPE  DATABASE        USER            ADDRESS                 METHOD
        host    all             all             0.0.0.0/0               md5

Restart the service

    # sudo systemctl stop postgresql
    # sudo systemctl start postgresql

Verification

    # psql -U postgres -W

    ## It will asking password for postgres user => Enter the password for the postgres

    postgres=# \l

Second Method:

    $ psql -d postgres -U postgres -W

Third Method:

    $  psql -d postgres -U postgres -h hostname -W 


![Installation Documentations](https://www.postgresql.org/download/linux/ubuntu/)

![Reference Documentations](https://github.com/FourTimes/Documentation/blob/master/postgres-db.md)