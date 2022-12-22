# Most Popular IPTABLES Command in Linux

In this article I will take you through most popular iptables commands in Linux. IPTABLES is a firewall built into Linux that allows a system administrator to define tables containing chains of rules that determine how network packets should be treated.

## Commands

- Open specific port:

  ```bash
    # You can change 443 to any port you want to open
    sudo iptables -I INPUT -p tcp -m tcp --dport 443 -j ACCEPT

    # save changes
    sudo netfilter-persistent save
  ```

- IP forwarding to use Iranian VPS as router to Internet

  ```bash
    # Just change the BRIDGE_IP and UPSTREAM_IP with your config
    sysctl net.ipv4.ip_forward=1
    iptables -t nat -A PREROUTING -p tcp --dport 22 -j DNAT --to-destination BRIDGE_IP # Current server (IRAN_VPS)
    iptables -t nat -A PREROUTING -j DNAT --to-destination UPSTREAM_IP # V2ray server or any server that has access to the free Internet
    iptables -t nat -A POSTROUTING -j MASQUERADE

    # Don't forget save the Iptables changes:
    sudo netfilter-persistent save
  ```
