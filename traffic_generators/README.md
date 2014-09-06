Generators
===

We use a few differen generic traffic generators.

(1) DPDK-Pktgen
https://github.com/justinemarie/Pktgen-DPDK
Can measure latency and throughput. Can read from pcaps.
Requires DPDK 1.5

(2) Netmap pkt-gen
https://code.google.com/p/netmap/
Runs on netmap, cannot read from pcap, only measures xput, unidirectional.

(2) Click
Click has two different random packet generators (infinite source and random source). Note that these two random generators are slow in a VM becuase they append timestamps to every packet, the latest versions of click have an option to disable this.

Click also has a FromDump which will read a pcap. But, the line rate is bottlenecked by the rate you can read the packets from disk. In this directory, there's a version of FromDump with a parameter BIGMEM that loads packets to memory at startup, and then loops through the packets in memory -- thus giving higher xput.

In general when testing for throughput though, use either the DPDK or netmap pkten.
