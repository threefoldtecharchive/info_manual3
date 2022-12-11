# What is a Threefold Gateway and Why Do We Need Them  

  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; There has been lots of discussion lately about Threefold Gateways, what they are, how they work, and why they are important to the future of the grid. as a general concept any node that is capable of receiving inbound traffic can function as a gateway for the grid in some capacity and the infrastructure provided by this is a major part of what makes the grid capable of creating a "virtual data center". which is fancy way of saying that we have the capability to make nodes that are geographically separated, and without public Ip addresses, behave as if they are on a local LAN network with each other. this is conceptually similar to a private VPN network. Where the grid differs from traditional technologies is its availability for endpoints within that network to be controlled autonomously.  

  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; A node becomes a "Gateway" when a Farmer adds a public ip address to the node itself on the dashboard, in doing this, that ip is then handed over to the base operating system of the node itself, in order for that I.P. address to be used in the overall functions of the grid, 

  

-  This differs from when an I.P that has been added to a farm is deployed with a workload in order for that workload to be accessible on the overall internet.  

  

This IP address is then used in providing Gateways for other nodes on the network to be able to receive inbound traffic in a private and low latency way. for instance a user can deploy a peer tube instance and have access to the website on a node/farm that does not have any public ipv4 addresses. this accomplished by the gateway nodes working in a fashion similar to a load balancer where a web server separates traffic based on the domain and forwards it to and from a node over the internal networks (Z-net and Planetary).  

  

A gateway node is also capable of participating in the overall mesh network, anytime a node comes online it has to join the network so that it is capable of being place into a private network with other nodes. This is accomplished by the node coming online sending an outgoing request to a gateway node to establish a "tunnel" that node then connects to the gateway, and holds open a connection so that at any time the gateway node can forward traffic to it. This relationship is similar to your home router and your computer, the gateway simply receives traffic and forwards it to the destination, then the process is reversed, to the user, it appears they connecting directly to the server with no public address.   

  

The concept of mesh networks has been around a long time, and while their popularity is growing, they have always suffered a shared flaw when expanded to a community level, they rely on each node within the system to be configured correctly, a misconfigured link in the chain can cause traffic to be diverted, intercepted or simply lost resulting in performance problems and security risks. Threefold Gateways provide the opportunity to solve this flaw, each gateway node is controlled by the blockchain allowing for configurations to be synced, and actively changes as performance needs necessitates. More importantly they provide a secure way for anyone to participate in the mesh, without exposing the contents of the traffic to the participants.  

  

Each gateway added to the network allows the grid to route traffic through their network, this allows the grid to utilize the transport infrastructure of that nodes i.s.p, as more and more gateways come online, we are able to choose from a wider selection of "routes" that traffic can be carried on in service of the grid. 
