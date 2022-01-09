# showcase scenario

Use HA proxy as a layer 4 Load Balancer.

## steps

1. install ha-proxy: `apt install haproxy`
2. install nodejs
3. configure server.js and haproxy.cfg on the guest VM
4. start nodejs script: `node server.js`
5. restart haproxy service: `sudo systemctl restart haproxy`
6. use your browser with guest VM IP and `80` port or curl `0.0.0.0:80`, you'll see response from different servers

[Original article][1]

[1]: https://serversforhackers.com/c/load-balancing-with-haproxy
