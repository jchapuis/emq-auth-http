emq-auth-http
=============

HTTP Auth/ACL Plugin for *EMQ* Broker

Build
-----

```
make && make tests
```

Configure the Plugin
--------------------

File: etc/emq_auth_http.conf

```
##--------------------------------------------------------------------
## Authentication request.
##
## Variables:
##  - %u: username
##  - %c: clientid
##  - %a: ipaddress
##  - %P: password
##
## Value: URL
auth.http.auth_req = http://127.0.0.1:8080/mqtt/auth
## Value: post | get | put
auth.http.auth_req.method = post
## Value: Params
auth.http.auth_req.params = clientid=%c,username=%u,password=%P

##--------------------------------------------------------------------
## Superuser request.
##
## Variables:
##  - %u: username
##  - %c: clientid
##  - %a: ipaddress
##
## Value: URL
auth.http.super_req = http://127.0.0.1:8080/mqtt/superuser
## Value: post | get | put
auth.http.super_req.method = post
## Value: Params
auth.http.super_req.params = clientid=%c,username=%u

##--------------------------------------------------------------------
## ACL request.
##
## Variables:
##  - %A: 1 | 2, 1 = sub, 2 = pub
##  - %u: username
##  - %c: clientid
##  - %a: ipaddress
##  - %t: topic
##
## Value: URL
auth.http.acl_req = http://127.0.0.1:8080/mqtt/acl
## Value: post | get | put
auth.http.acl_req.method = get
## Value: Params
auth.http.acl_req.params = access=%A,username=%u,clientid=%c,ipaddr=%a,topic=%t
```

Load the Plugin
---------------

```
./bin/emqttd_ctl plugins load emq_auth_http
```

HTTP API
--------

200 if ok

4xx if unauthorized

License
-------

Apache License Version 2.0

Author
------

EMQ X Team.

