# Most Popular IPTABLES Command in Linux

In this article I will take you through most popular iptables commands in Linux. IPTABLES is a firewall built into Linux that allows a system administrator to define tables containing chains of rules that determine how network packets should be treated.

## Commands

- Open specific port:

  ```bash
    sudo iptables -I INPUT -p tcp -m tcp --dport 443 -j ACCEPT
    # save changes
    sudo netfilter-persistent save
  ```
