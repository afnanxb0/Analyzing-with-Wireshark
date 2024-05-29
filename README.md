# Analyzing-with-Wireshark

This is a very basic analysis with wireshark. I have performed a depth ananlysis with this tool on my BTL1 Certificate.

<a href="https://elearning.securityblue.team/public/lab-certificate/730caf39-a177-43c1-ab73-560abadd4eb2">Wireshark Network Investigations</a> - Taking advantage of major Wireshark features to improve and assist in in-depth manual analysis

# Project description
I analyzed a network packet capture file that contains traffic data related to a user connecting to an internet site. The ability to filter network traffic using packet sniffers to gather relevant information is an essential skill as a security analyst.
I filtered the data in order to:
    • identify the source and destination IP addresses involved in this web browsing session,
    • examine the protocols that are used when the user makes the connection to the website, and
    • analyze some of the data packets to identify the type of information sent and received by the systems that connect to each other when the network data is captured.


# Explore data with Wireshark


In this task, I displayed the contents of each of these files. Then I generated a hash value for each of these files and send the values to new files, which I use to examine the differences in these values later. 
I scrolled down the packet list until a packet is listed where the info column starts with the words 'Echo (ping) request' to find out the protocol which is ICMP
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2018-49-05.png" alt="GitHub" style="width:1423px;height:auto;"> </a>

# Apply a basic Wireshark filter and inspect a packet

Here, I open a packet in Wireshark for more detailed exploration and filter the data to inspect the network layers and protocols contained in the packet.
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2018-52-17.png" alt="GitHub" style="width:1423px;height:auto;"> </a>

<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2018-57-28.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
The upper section of this window contains subtrees where Wireshark will provide you with an analysis of the various parts of the network packet. The lower section of the window contains the raw packet data displayed in hexadecimal and ASCII text. There is also placeholder text for fields where the character data does not apply, as indicated by the dot (“.”).
Transmission Control Protocol subtree. provides detailed information about the TCP packet, including the source and destination TCP ports, the TCP sequence numbers, and the TCP flags.
The source port and destination port listed here match the source and destination ports in the info column of the summary display for this packet in the list of all of the packets in the main Wireshark window. 80 is the TCP destination port of this TCP packet. 

# Use filters to select packets
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2018-59-22.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-00-07.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-07-36.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-08-11.png" alt="GitHub" style="width:1423px;height:auto;"> </a>

The protocol contained in the Internet Protocol Version 4 subtree from the first packet related to MAC address 42:01:ac:15:e0:02 is TCP.

# Use filters to explore DNS packets
I used filters to select and examine DNS traffic. Once I’ve selected sample DNS traffic, I drilled down into the protocol to examine how the DNS packet data contains both queries (names of internet sites that are being looked up) and answers (IP addresses that are being sent back by a DNS server when a name is successfully resolved).
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-09-13.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-10-04.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
Domain Name System (query) is opensource.google.com
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-12-53.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-14-02.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
The Answers data includes the name that was queried (opensource.google.com) and the addresses that are associated with that name. The IP address is 142.250.1.139.


# Use filters to explore TCP packets
In this task, I used additional filters to select and examine TCP packets to search for text that is present in payload data contained inside network packets. This will locate packets based on something such as a name or some other text that is of interest.

<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-15-21.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-16-38.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
The Time to Live value of the packet as specified in the Internet Protocol Version 4 subtree is 64
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-19-13.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
The Frame Length of the packet as specified in the Frame subtree is 54 bytes.
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-19-46.png" alt="GitHub" style="width:1423px;height:auto;"> </a>
The Header Length of the packet as specified in the Internet Protocol Version 4 subtree is 20 bytes.
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-20-10.png" alt="GitHub" style="width:1423px;height:auto;"> </a>

The Destination Address as specified in the Internet Protocol Version 4 subtree is 169.254.169.254.
<a href="https://github.com/afnanxb0"> <img src="https://github.com/afnanxb0/Analyzing-with-Wireshark/blob/main/Screenshot%20from%202023-09-10%2019-21-23.png" alt="GitHub" style="width:1423px;height:auto;"> </a>


# Summary
First, I opened the packet capture file and explore the basic Wireshark graphic user interface. Second, I opened a detailed view of a single packet and explore how to examine the various protocol and data layers inside a network packet.Third, I applied filters to select and inspect packets based on specific criteria. Fourth, I filtered and inspect UDP DNS traffic to examine protocol data. Finally, I applied filters to TCP packet data to search for specific payload text data.

