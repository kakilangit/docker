Docker for MariaDB 10.2.7 with OQGraph
====================

[![](https://images.microbadger.com/badges/image/kakilangit/mariadb:10.2.svg)](http://microbadger.com/images/kakilangit/mariadb "Get your own image badge on microbadger.com")

Docker image to run a MariaDB database server with OQGraph.

Usage
-----

To create the image `kakilangit/mariadb`, execute the following command:

        docker build -t kakilangit/mariadb .

To run the image and bind to port 3306:

        docker run -d -p 3306:3306 kakilangit/mariadb

The first time that you run your container, a new user `admin` with all privileges
will be created in MariaDB with a random password. To get the password, check the logs
of the container by running:

        docker logs <CONTAINER_ID>

You will see an output like the following:

        ========================================================================
        You can now connect to this MariaDB Server using:

            mysql -uadmin -pAnuAnuan -h<host> -P<port>

        Please remember to change the above password as soon as possible!
        MariaDB user 'root' has no password but only allows local connections
        ========================================================================


In this case, `AnuAnuan` is the password assigned to the `admin` user.

Done!


Setting a specific password for the admin account
-------------------------------------------------

If you want to use a preset password instead of a random generated one, you can
set the environment variable `MARIADB_PASS` to your specific password when running the container:

        docker run -d -p 3306:3306 -e MARIADB_PASS="mypass" kakilangit/mariadb


Mounting the database file volume from other containers
------------------------------------------------------

One way to persist the database data is to store database files in another container.
To do so, first create a container that holds database files:

    docker run -d -v /var/lib/mysql --name dbvolume -p 22:22 debian

This will create a new ssh-enabled container and use its folder `/var/lib/mysql` to store MariaDB database files.
You can specify any name of the container by using `--name` option, which will be used in next step.

After this you can start your MariaDB image using volumes in the container created above (put the name of container in `--volumes-from`)

    docker run -d --volumes-from dbvolume -p 3306:3306 kakilangit/mariadb

TokuDB
------

TokuDB is optional. Remove comment on my.cnf line 169 to enable TokuDB Engine.
Disabling Transparent HugePage Support for TokuDB support on your Host.

  https://mariadb.com/kb/en/mariadb/enabling-tokudb/#check-for-transparent-hugepage-support-on-linux
