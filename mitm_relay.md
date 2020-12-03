# mitm_relay TCP Interceptor

## simple mitm
python3 mitm_relay.py -r [udp:|tcp:]lport:rhost:rport
python3 mitm_relay.py -r tcp:443:example.com:443

## proxy with burp
python3 mitm_relay.py -r [udp:|tcp:]lport:rhost:rport -p 127.0.0.1:8080
python3 mitm_relay.py -r tcp:443:example.com:443 -p 127.0.0.1:8080