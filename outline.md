# ECE416 Research Project Outline

1. Course Number: ECE416
2. Term: Winter, 2017
3. Student name:  Xiaowei, Huang (20481376/x68huang)
4. Title of the report: BBR congestion control algorithm and its usage on the Internet

## TCP BBR congestion control alogrithim and its usage on the Internet

### Outline

The Transmission Control Protocol (TCP) is one of the main protocols of the Internet protocol suite, TCP provides reliable, ordered, error-checked delivery of data stream between applications on the Internet. Major Internet Application such as WWW, Email relies on TCP. Network congestion occurs when a network node is carrying more data than it can handle which causes queueing delay, packet loss and blocking on new connections. Network congestion is a typical problem in network architecture design and cannot be solved by just upgrading infrastructure. TCP uses a network congestion-avoidance algorithm to avoid network congestion. The standard TCP congestion control algorithm can be found in RFC 2581. The document specifies for standard congestion control algorithm. However, TCP has changed very little since its initial design in the 1980s. As the evolution of Internet and Information explosion, the classical congestion control algorithm may not be suitable for the long-distance, high latency TCP connections that exist everywhere nowadays. This report discusses a new TCP congestion control algorithm developed by Google and illustrates its usage on the Internet.

The Internet has predominantly used loss-based congestion control(Reno or CUBIC) since the 1980s. Loss-based congestion control relies on packet loss rate as the signal to slow down. Ssuch algorithm worked well for many years, in today's network it is unfortunately out-date. Loss-based congestion control causes the infamous bufferbloat problem, which causes seconds of needless queueing delay in packet-switched networks.

Google's BBR congestion control algorithm aims to solve the bufferbloat problem, which is common nowadays in long-distance, high packet loss rate network. Unlike loss-based congestion control, BBR uses an explicit model of the network pipe by sequentially probing the bottleneck bandwidth and RTT. This method resolve the ambiguity between single bandwidth measurement and propagation delay measurement, helping find an optimal operating point for the whole network. BBR congestion algorithm has been pushed to Linux Kernel mainline(v4.9). It is considered as a candidate to replace the default congestion control algorithm(CUBIC).

In my report I am going to give a brief introduction the BBR algorithm followed by a brief algorithm analysis. A detailed test will be conducted to compare CUBIC(Linux default) and BBR algorithm. I will set up a long latency, high packet loss rate connection host using a VPS setup somewhere in South East Asia. Then I will perform some TCP file transfer to test the transmission speed using different congestion control on the host. Using the data I gather I can prove the correctness of my hypotheisis that 'BBR is a better congestion control algorithm compared to CUBIC'. After that I will analysis drawback of BBR algorithm. Last part of the report will be discussion section, in which I will discuss the prospects of BBR algorithm.

Proposed Report Structure:

1. Introduction to BBR algorithm
2. Algorithm analysis
3. Detailed test (Comparsion between BBR and CUBIC)
4. Drawback about BBR algorithm
5. Discussion on future prospect

## Reference
1. [Linux Kernel - next networking tree](http://git.kernel.org/cgit/linux/kernel/git/davem/net-next.git/commit/?id=0f8782ea14974ce992618b55f0c041ef43ed0b78)
2. [RFC 2581](https://tools.ietf.org/html/rfc2581)
3. [BBR: Congestion-Based Congestion Control](http://queue.acm.org/detail.cfm?id=3022184)
