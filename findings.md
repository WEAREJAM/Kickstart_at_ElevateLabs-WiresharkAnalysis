# Wireshark analysis

Wireshark is a powerful tool where we can see how the data flows and how it reaches from the client to and server. This information seems less important, but NO this is where we get information by just capturing the packets. Let's say i captured the packets and i observed 80 port being open and used.

Note: Port 80 is not a secure port, the transferred data between client and server is transparent. The sensitive information is clearly visible in this port. Every request we send deals with the right port and protocols.

Example 1: PING SCAN ANALYSIS

Let's see how Wireshark responds with a simple ping scan. [ICMP]

> ping -4 google.com

![Wireshark example](https://github.com/WEAREJAM/Kickstart_at_ElevateLabs-WiresharkAnalysis/blob/main/assets/sample1.png?raw=true)

The above image shows the simple ping scan. This scan is where we as client request the server and the server responds if it is live/active. 

If you observe the below data we can clearly see the tcp protool here adn the hexa data is on the left. all the readings seems random but deeply connected and say the same. the destination, source ip address and other info can be seen along with mac addresses. 

Example 2: TCP SCAN ANALYSIS

Lets see the behaviour with the noisiest TCP scan. The TCP scan is mostly known as three way handshake. This scan is mostly avoided so it doesnt create more and more packets and make the server unavailable. This behaviour is also called DOS attack. 

In this handshake client sends SYN packet if open it expects SYN/SCK by server, later responds with an ACK and RST/ACK. Such continuous interaction creates n number of packets.

> nmap -sT targetip

![Wireshark example](https://github.com/WEAREJAM/Kickstart_at_ElevateLabs-WiresharkAnalysis/blob/main/assets/sample2.png?raw=true)

the wireshark is just an packet catcher but not an analyzer it is out job to get to the crucial part. 

So can i capture any traffic? YES, AND CAN ALSO SAVE THE TRAFFIC AND ANALYZE LATER.

Example 3: DNS SCAN ANALYSIS

![Wireshark example](https://github.com/WEAREJAM/Kickstart_at_ElevateLabs-WiresharkAnalysis/blob/main/assets/sample3.png?raw=true) 

Note: The DNS port is the most common port; the dns stands for Domain Name System. So how every word/spell do return webpages? 

The answer is DNS

Process:

_Client_: Ok search engine, I want google.com

__DNS Resolver : Sure lets ask IP address for DNS resolver__

_DNS Resolver to root DNS_: Whats ip to google.com?

_Root DNS_: I dont know IP address!!! But I know in which server it is stored on: TLD name server

__DNS Resolver : Ok__

_DNS Resolver to TLD Name server_: so whats ip to google.com?

_TLD Name server_: Hmmm!!! I do know the authoritative name, check there.

__DNS Resolver : oh!! OK__

_DNS Resolver to authoritative DNS resolver_: So whats the ip to google.com?

_Authoritative DNS_: Yeah i do know that. Here its ip address //8.8.8.8

__SO EVERY TIME I BROWSE GOOGLE, DOES DNS FOLLOW THE SAME PROCESS?? NOPE. THE DNS IS DESIGNED THE WAY THAT IT REMEMBERS THE ALREADY BROWSED WEBSITES WITH IP ADDRESS__. _The process follows when only a new website is browsed_

The above image is an example to this there we see only few interactions in port 53. 

The resolver asked what the ipv4 and ipv6 address to that website. and it replies with the ip. 

The total packets can be seen here in Wireshark. 



