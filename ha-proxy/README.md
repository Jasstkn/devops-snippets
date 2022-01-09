# ha-proxy

[source](https://www.digitalocean.com/community/tutorials/an-introduction-to-haproxy-and-load-balancing-concepts)

## HA proxy terminology

### Access Control List (ACL)

ACL provides a flexible solution to perform content switching and generally to take decisions based on content extracted
from the request, the response or any environmental status. The principle issimple :

- define test criteria with sets of values
- perform actions only if a set of tests is valid

```bash
acl <aclname> <criterion> [flags] [operator] <value> ...
```

### Backend

A backend is a set of servers that receives forwarded requests.

In its most basic form, a backend can be defined by:

- which load balance algorithm to use
- a list of servers and ports

### Frontend

A frontend defines how requests should be forwarded to backends.

Their definitions are composed of the following components:

- a set of IP addresses and a port (e.g. 10.1.1.7:80, *:443, etc.)
- ACLs
- `use_backend` rules, which define which backends to use depending on which ACL conditions are matched, and/or a `default_backend` rule that handles every other case

## Load Balancing Algorithms

1. **roundrobin** - Round Robin selects servers in turns. This is the default algorithm.
2. **leastconn** - Selects the server with the least number of connections–it is recommended for longer sessions. Servers in the same backend are also rotated in a round-robin fashion.
3. **source** - This selects which server to use based on a hash of the source IP i.e. your user’s IP address. This is one method to ensure that a user will connect to the same server.

## Sticky Sessions

Some applications require that a user continues to connect to the same backend server. This persistence is achieved through sticky sessions, using the `appsession`.

## Health Check

HAProxy uses health checks to determine if a backend server is available to process requests.
