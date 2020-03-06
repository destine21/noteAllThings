HTTPS traffic interception (Flutter, Xamarin?)
1. (Android only) Bypass SSL validation (https://blog.nviso.be/2019/08/13/intercepting-traffic-from-android-flutter-applications)
2.1 (Android) Set up a PPTP VPN server on a Linux host (http://www.flinkd.org/wp-content/uploads/2013/09/pptp.txt)
2.2 (iOS) Set up an L2TP VPN server on a Linux host
3. Configure iptables on the Linux host:

$ iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to-destination <proxy-ip>:<proxy-port>
$ iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 443 -j DNAT --to-destination <proxy-ip>:<proxy-port>

4. Configure a device to connect to the VPN server
5. Enable invisible proxy on the proxy's listening ports