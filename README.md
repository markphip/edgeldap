SVN Edge LDAP Test Environment
==============================

This is a Docker Compose setup that includes SVN Edge latest devbuild from Docker Hub
plus an OpenLDAP server. This can be used to test SVN Edge with an LDAP Server, including
TLS connections.

Run the Server
--------------

To run this just clone this repository and run: `docker-compose up`. This will start the
SVN Edge and LDAP servers and load the LDAP schema with a few test users:

| Username  	| Password  	|
|---	|---	|
| arnold    | arnold    |
| testuser1 | test123   |
| testuser2 | test123   |

Configure SVN Edge
------------------

After starting the server go to http://localhost:3343 and login as `admin / admin`. Then
go to `Administration` > `Authentication` to configure LDAP. These settings should work:

```
LDAP Security Level: STARTTLS
LDAP Server Host: ldap
LDAP Server Port: 636
LDAP Base DN: ou=people,dc=example,dc=org
LDAP Bind DN: cn=admin,dc=example,dc=org
LDAP Bind Password: admin
LDAP Search Scope: sub
LDAP Filter: objectClass=person
```

Once these settings are entered it ought to be possible to authenticate to SVN or ViewVC using
any of the LDAP usernames and passwords listed in the table above.
