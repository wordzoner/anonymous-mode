## Anonymous-Mode
> $ git clone https://github.com/yuu0910/anonymous-mode/

> $ cd ./anonymous-mode/

> $ chmod 0755 ./anonymous

## Help
> $ sudo ./anonymous

## Stop
> $ sudo ./anonymous stop

## Start
> $ sudo ./anonymous start debian-tor

## Restart
> $ sudo ./anonymous restart

## Start Arch Linux (Beta)

> $ sudo ./anonymous start tor

## Anonymous-Mode DNS Only
> $ chmod 0755 ./firewall

> $ sudo ./firewall start debian-tor

## Anonymous-Mode Diff Anonymous Firewall

```diff
--- ./anonymous 2022-07-26 02:19:16.294297014 +0000
+++ ./firewall  2022-07-28 05:27:56.169252161 +0000
@@ -217,6 +217,8 @@
   iptables -t nat -A OUTPUT -p tcp -d 10.192.0.0/10 --syn -j DNAT --to-destination='127.0.0.1:9040'
 
   iptables -t nat -A OUTPUT -m owner --uid-owner $1 -j RETURN
+  iptables -t nat -A OUTPUT -p tcp --dport 443 -j RETURN
+  iptables -t nat -A OUTPUT -p tcp --dport 80 -j RETURN
   iptables -t nat -A OUTPUT -o lo -j RETURN
 
   for sp in $SP; do
@@ -248,6 +250,8 @@
   iptables -A OUTPUT -p tcp -d 127.0.0.1 --dport 9040 --syn -j ACCEPT
 
   iptables -A OUTPUT -p tcp -m owner --uid-owner $1 -m state --state NEW --syn -j ACCEPT
+  iptables -A OUTPUT -p tcp --dport 443 --syn -j ACCEPT
+  iptables -A OUTPUT -p tcp --dport 80 --syn -j ACCEPT
   iptables -A OUTPUT -o lo -j ACCEPT
 
   for sp in $SP; do
```
