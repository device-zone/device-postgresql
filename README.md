# device-postgresql
Provides a PostgreSQL database server appliance.

This appliance does the following:

- All parameters passed to the device commands are syntax checked and canonicalised, with bash completion.
- Creates database instances as required, running on individual ports.
- Automatically creates databases within instances as required.
- Binds securely to the unix domain socket /run/postgresql/.s.PGSQL.[port].
- Autostarts on server restart.
- Zero Trust configuration.

## before

- Deploy the device-postgresql package.

```
[root@server ~]# dnf install device-postgresql
```

## add instance

To add an instance called "seawitch" running on port 5432, run this.

```
[root@server ~]# device services db postgresql instance add name=seawitch port=5432
```

In the absence of any TLS configuration, the instance uses the port number to
make the unix domain sockets unique on the machine. As a result, the port number
needs to be specified even if there is no intention of exposing the port over the
network.

## remove instance

To remove an instance called "seawitch", run this.

```
[root@server ~]# device services db postgresql instance remove seawitch
```

The data directory when removing an instance is moved into the postgresql backup
directory, and needs to be removed manually.

## add database

To add a database called "things", run this.

```
[root@server ~]# device services db postgresql database add name=things local-owner=things locale=C.utf8 
```

## remove database

To remove a database called "things", run this.

```
[root@server ~]# device services db postgresql database remove things 
```


