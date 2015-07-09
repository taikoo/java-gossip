The current implementation of the gossip service is selecting the member to gossip with purely random. We are planning to extends this implementation so one can choose how the gossiping is done. We will provide a implementation based on the network-friendly version proposed by Serby et al.<sup>1</sup>.

## Testing ##
The current implementation can be downloaded on the right side of this page (java-gossip-0.1.zip). You can simply edit the gossip.conf to your local configuration; copy the folder and start two gossip clients who are talking to eachother. You can add as many clients as you want. You can run multiple gossip clients per host by specifying the same IP address but a different port.

## API ##
You can also download the source of this implementation when you want to integrate the gossip service into your application. Look at the com.google.code.gossip.examples.GossipExample class for a example of how to use the gossip service.

### A code example ###
First create a list of gossip members who will all be gossiping together.
```
ArrayList<GossipMember> startupMembers = new ArrayList<GossipMember>();
startupMembers.add(new RemoteGossipMember("192.168.1.100", 2222));
startupMembers.add(new RemoteGossipMember("192.168.1.101", 2222));
startupMembers.add(new RemoteGossipMember("192.168.1.103", 2222));
```

Now create the local gossip service who will be gossiping with these members.
```
GossipService gossipService = new GossipService(2222, LogLevel.DEBUG, startupMembers, new GossipSettings());
```

Everything is set, so now we can start the gossip service.
```
gossipService.start();
```

## Problems ##
If you discover problems or have a suggestion, please file them at the Issues tab.

## Acknowledgements ##
This implementation is based on the former made implementation [gossip-protocol-java](http://code.google.com/p/gossip-protocol-java/).


<sup>1</sup>. "Network-Friendly Gossiping", Sabina Serbu, Étienne Riviѐre and Pascal Felber, Lecture Notes In Computer Science; Vol. 5873.
[@ACM](http://portal.acm.org.proxy.library.uu.nl/citation.cfm?id=1693564.1693611)