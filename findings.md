# Wireshark analysis

Wireshark is a powerful tool where we can see how the data flows and how it reaches from the client to and server. This information seems less important, but NO this is where we get information by just capturing the packets. Let's say i captured the packets and i observed 80 port being open and used.
Note: Port 80 is not a secure port, the transferred data between client and server is transparent. The sensitive information is clearly visible in this port. Every request we send deals with the right port and protocols.

Example 1: 
Let's see how Wireshark responds with a simple ping scan. [ICMP]

> ping -4 google.com

sample1 

The above image shows the simple ping scan. This scan is where we as client request the server and the server responds if it is live/active. 
If you observe the below data we can clearly see the tcp protool here adn the hexa data is on the left. all the readings seems random but deeply connected and say the same. the destination, source ip address and other info can be seen along with mac addresses. 

Example 2:
Lets see the behaviour with the noisiest TCP scan. The TCP scan is mostly known as three way handshake. This scan is mostly avoided so it doesnt create more and more packets and make the server unavailable. This behaviour is also called DOS attack. 
In this handshake client sends SYN packet if open it expects SYN/SCK by server, later responds with an ACK and RST/ACK. Such continuous interaction creates n number of packets.

> nmap -sT <ip address>

sample 2

Example 3:



