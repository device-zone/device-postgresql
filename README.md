# device-postgresql
Provides a PostgreSQL database server appliance.

This appliance does the following:

- All parameters passed to the device commands are syntax checked and canonicalised, with bash completion.
- Automatically creates databases within the default instance  as required.
- Binds securely to the unix domain socket /run/postgresql/.s.PGSQL.5432.
- Autostarts on server restart.
- Zero Trust configuration.

## before

- Deploy the device-postgresql package.

```
[root@server ~]# dnf install device-postgresql
```

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


