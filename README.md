# CN_Orange_Project
SDN Controller Project Report (Mininet + POX) 

By: 

 
Sumit Nagaraj Bali - PES1UG24AM453 

Zayaan Ahmed – PES1UG24AM457 

Anagha Kaushik- PES1UG24AM459 

 

 

 

1. Problem Statement 

The objective of this project is to design and implement a Software Defined Networking (SDN) environment using Mininet and a POX controller. The system should: 

Create a custom network topology 

Implement SDN control logic using OpenFlow 

Enable communication between hosts 

Monitor network behavior (traffic, packets, flows) 

Evaluate performance using ping and iperf 

 

2. Setup and Execution Steps 

Step 1: Environment Setup 

Installed Mininet 

Installed POX controller 

Used Python 3.10 for compatibility 

Step 2: Start POX Controller 

Command used: 

python3.10 pox.py log.level --DEBUG openflow.of_01 forwarding.l2_learning monitor_pox 
 

Step 3: Create Mininet Topology 

Command used: 

sudo mn --topo linear,3 --controller=remote,ip=127.0.0.1,port=6633 --switch ovsk,protocols=OpenFlow10 
 

Topology: 

3 hosts (h1, h2, h3) 

3 switches (s1, s2, s3) 

Linear connection 

 

3. Expected Output 

Hosts should successfully communicate (pingall = 0% loss) 

Controller should install flow rules dynamically 

Monitoring logs should display packet and byte counts 

iperf should measure bandwidth between hosts 

 

4. Proof of Execution 

4.1 Mininet Setup and Ping Results 

 

Observation: 

All hosts successfully communicated 

0% packet loss observed 

 

4.2 Controller Logs  

Observation: 

Switch connections established 

Flow rules installed dynamically 

Continuous network utilization logs displayed 

 

4.3 Packet Processing and Forwarding Logs 

 

 

Observation: 

Packet parsing activity observed 

MAC-based forwarding rules installed 

Learning switch behavior verified 

 

4.4 Monitoring Output 

 

 

 

Observation: 

Packet counts and byte statistics printed periodically 

Confirms monitoring module is working 

 

 

5. SDN Logic and Flow Rule Implementation 

Learning Switch Logic 

Controller learns MAC → port mapping 

Stores mapping in a table 

For unknown destination → floods packet 

For known destination → installs flow rule 

Flow Rule Structure 

Match: source MAC, destination MAC 

Action: forward to specific port 

Priority: default 

 

6. Functional Correctness 

The project successfully demonstrates: 

Packet forwarding (Learning Switch) 

Dynamic flow installation 

Monitoring and logging 

End-to-end host communication 

 

7. Performance Observation and Analysis 

Latency (Ping) 

Observed using: 

pingall 
 

Result: 0% packet loss 

Throughput (iperf) 

Measured using: 

iperf h1 h3 
 

Flow Table Behavior 

Initial packets trigger controller 

Subsequent packets handled by switches directly 

Packet Statistics 

Periodic logs show packet count and byte usage 

 

8. Explanation and Validation 

Controller correctly handles packet_in events 

Flow rules installed as expected 

Network behaves like a Layer 2 learning switch 

Monitoring module validates traffic flow 

Validation checks: 

Ping success 

Flow installation logs 

Monitoring outputs 

 

9. Conclusion 

The SDN environment was successfully implemented using Mininet and POX. The controller effectively manages network traffic, installs flow rules, and monitors network behavior. The project meets all required evaluation criteria. 

 

10. References 

Mininet Documentation 

POX Controller Documentation 

OpenFlow Specification 

 

 
