# Intelligent Computer Network Simulator

A Java-based, CLI-first Computer Network Simulator designed to simulate how computer networks operate internally. The project combines **Computer Networks, Data Structures and Algorithms (DSA), Object-Oriented Programming (OOP), Rule-Based Intelligent Systems, and Basic Machine Learning**.

The goal is to develop a simplified Packet Tracer-like environment where users can create network devices, establish connections, configure communication protocols, transmit messages, simulate packet delivery, and analyze network performance.

The system will also explore how intelligent algorithms can help make network-related decisions, such as selecting routes, identifying congestion, prioritizing packets, and predicting network conditions.

---

# 1. Project Objectives

The main objectives are:

- Simulate communication between computers and network devices.
- Create and configure PCs, routers, and switches.
- Establish connections between network devices.
- Simulate TCP and UDP communication.
- Understand packet formation, segmentation, transmission, and reassembly.
- Implement reliable data transfer mechanisms.
- Simulate packet loss, delay, timeout, acknowledgments, and retransmissions.
- Implement routing algorithms to determine suitable paths.
- Apply DSA concepts to manage network operations.
- Develop intelligent mechanisms for network optimization.
- Implement basic machine learning algorithms from scratch in Java.
- Collect network statistics and evaluate communication performance.

# 2. Project Features

## 2.1 Network Topology Management

Users will be able to:

- Create computers (PCs).
- Create routers.
- Create switches.
- Connect devices using network links.
- Define link properties such as bandwidth, delay, and status.
- View connected devices.
- Create different network topologies.

Example:

```text
        PC1
         |
      Switch1
       /   \
    PC2    Router1
              |
           Router2
              |
             PC3
```

## 2.2 Communication System

The communication module will simulate how two devices exchange information over a network.

A user will select a source device, destination device, message, and communication protocol.

The communication process will involve:

1. Application creates a message.
2. Transport layer processes the message.
3. TCP or UDP divides the data into segments.
4. Network layer creates IP datagrams.
5. Routing determines the next hop.
6. Data-link layer creates frames.
7. Network devices forward the frames.
8. The destination receives the transmitted data.
9. The receiving layers process and reassemble the data.
10. The destination application receives the original message.

### Communication Protocols

**TCP (Transmission Control Protocol)**

The TCP module will simulate:

- Connection establishment.
- Three-way handshake.
- Data segmentation.
- Sequence numbers.
- Acknowledgment numbers.
- Sender and receiver buffers.
- Sliding window.
- Stop-and-Wait.
- Go-Back-N.
- Selective Repeat.
- Timeout and retransmission.
- Reliable data delivery.
- Connection termination.

**UDP (User Datagram Protocol)**

The UDP module will simulate:

- Connectionless communication.
- Datagram creation.
- Port-based delivery.
- Datagram transmission.
- Packet loss.
- Delay.
- No acknowledgment-based reliability mechanism.

### TCP Three-Way Handshake

```text
       CLIENT                         SERVER
          |                              |
          | -------- SYN --------------> |
          |                              |
          | <----- SYN + ACK ----------- |
          |                              |
          | -------- ACK --------------> |
          |                              |
          |       CONNECTION             |
          |       ESTABLISHED            |
```

### Example Communication

```text
Source: PC1
Destination: PC3
Protocol: TCP
Message: Hello Network
```

Expected simulated process:

```text
PC1
 |
 | Create Message
 |
TCP Layer
 |
 | Divide Message into Segments
 |
IP Layer
 |
 | Create IP Datagrams
 |
Routing
 |
 | Select Next Hop
 |
Router1
 |
 | Forward Packet
 |
Router2
 |
 | Forward Packet
 |
PC3
 |
 | Receive and Reassemble
 |
Original Message: Hello Network
```

*This is a conceptual communication flow. The implementation will determine the actual behavior and supported features.*

## 2.3 Packet Management

The packet module will manage:

- Message creation.
- Packet segmentation.
- Packet headers.
- Source and destination addresses.
- Source and destination ports.
- Sequence numbers.
- Acknowledgment numbers.
- Packet size.
- Packet priority.
- Packet status.
- Packet reassembly.

The simulator will use custom data structures where appropriate rather than relying on Java's predefined collection classes for core DSA implementations.

## 2.4 Routing System

The routing module will determine how packets travel from source to destination.

Planned algorithms:

- Breadth-First Search (BFS).
- Depth-First Search (DFS).
- Dijkstra's Shortest Path Algorithm.
- Bellman-Ford Algorithm.

Routing features:

- Static routing.
- Dynamic routing.
- Routing tables.
- Next-hop selection.
- Alternative route selection.
- Link failure handling.

## 2.5 Network Performance Simulation

The simulator will collect and display:

- Total packets sent.
- Total packets received.
- Packets lost.
- Successful delivery rate.
- Packet delay.
- Transmission time.
- Retransmission count.
- Queue length.
- Bandwidth utilization.
- Congestion level.

## 2.6 Intelligent Network Management

The intelligent system will help make decisions using network conditions.

Initial intelligent features will use rule-based logic and algorithms.

Examples:

- Detecting possible network congestion.
- Selecting alternative routes.
- Prioritizing important packets.
- Identifying unusual packet loss.
- Recommending a suitable communication protocol.
- Detecting failed network links.

The intelligent module will recommend decisions. The network engine will execute the actual forwarding and transmission operations.

## 2.7 Basic Machine Learning

Machine learning will be introduced after the networking foundation is working.

Planned algorithms:

- Linear Regression.
- Logistic Regression.
- K-Nearest Neighbors (KNN).
- Decision Trees.

Possible applications:

| ML algorithm | Possible application |
|---|---|
| Linear Regression | Predict network delay |
| Logistic Regression | Predict congestion or no congestion |
| KNN | Classify network conditions |
| Decision Tree | Recommend network actions |

The simulator can generate its own training dataset from simulated network activity.

Possible dataset attributes:

- Packet arrival rate.
- Packet delivery rate.
- Queue utilization.
- Average delay.
- Packet loss rate.
- Available bandwidth.
- Congestion status.

Machine learning algorithms will initially be implemented from scratch in Java, using arrays and mathematical operations rather than external ML libraries.

**Neural Networks and Deep Learning are not part of the initial implementation.** They may be considered as future enhancements.

---

# 3. Project Architecture and Module Organization

The project will follow a modular architecture. Each module will have its own responsibilities, and classes will communicate through clearly defined methods.

Suggested package structure:

```text
NetworkSimulator/
│
├── src/
│   │
│   ├── Main.java
│   │
│   ├── network/
│   │   ├── Device.java
│   │   ├── Computer.java
│   │   ├── Router.java
│   │   ├── Switch.java
│   │   ├── Network.java
│   │   └── NetworkLink.java
│   │
│   ├── communication/
│   │   ├── CommunicationManager.java
│   │   ├── Sender.java
│   │   ├── Receiver.java
│   │   ├── Message.java
│   │   └── PortManager.java
│   │
│   ├── packet/
│   │   ├── Packet.java
│   │   ├── Segment.java
│   │   ├── IPDatagram.java
│   │   ├── Frame.java
│   │   ├── PacketHeader.java
│   │   └── PacketManager.java
│   │
│   ├── protocols/
│   │   ├── Protocol.java
│   │   ├── TCP.java
│   │   ├── UDP.java
│   │   ├── TCPConnection.java
│   │   ├── Acknowledgment.java
│   │   ├── SenderBuffer.java
│   │   ├── ReceiverBuffer.java
│   │   ├── TimerManager.java
│   │   ├── SlidingWindow.java
│   │   ├── GoBackN.java
│   │   └── SelectiveRepeat.java
│   │
│   ├── routing/
│   │   ├── RoutingManager.java
│   │   ├── RoutingTable.java
│   │   ├── Route.java
│   │   ├── Dijkstra.java
│   │   └── BellmanFord.java
│   │
│   ├── dsa/
│   │   ├── CustomLinkedList.java
│   │   ├── CustomQueue.java
│   │   ├── CircularQueue.java
│   │   ├── PriorityQueue.java
│   │   ├── Heap.java
│   │   └── Graph.java
│   │
│   ├── intelligence/
│   │   ├── IntelligentManager.java
│   │   ├── CongestionDetector.java
│   │   ├── PacketClassifier.java
│   │   ├── RouteAdvisor.java
│   │   └── AnomalyDetector.java
│   │
│   │
│   ├── simulation/
│   │   ├── SimulationEngine.java
│   │   ├── NetworkClock.java
│   │   ├── EventManager.java
│   │   └── NetworkMetrics.java
│   │
│   └── ui/
│       ├── ConsoleMenu.java
│       └── OutputManager.java
│
└── README.md
```

This is the proposed organization. Classes can be added, renamed, or split as the implementation becomes more detailed.

---

# 4. Module-Wise Class Descriptions

## Module 1: Network Management

This module is responsible for creating and managing network devices and their connections.

| Class | Responsibility | Important methods |
|---|---|---|
| Device | Base class for network devices | `getId()`, `getIPAddress()`, `sendPacket()` |
| Computer | Represents an end device | `createMessage()`, `receiveData()` |
| Router | Forwards packets between networks | `forwardPacket()`, `getNextHop()` |
| Switch | Connects devices within a LAN | `forwardFrame()`, `learnMAC()` |
| Network | Manages the overall topology | `addDevice()`, `connectDevices()`, `displayTopology()` |
| NetworkLink | Represents a connection between two devices | `setStatus()`, `getDelay()`, `getBandwidth()` |

**Class relationship:**

```text
             Device
                |
       -------------------
       |        |        |
    Computer  Router   Switch

                |
             Network
                |
           NetworkLink
```

`Computer`, `Router`, and `Switch` inherit common properties from `Device`.

The `Network` class manages devices and their connections.

## Module 2: Communication Management

This module controls the communication process between source and destination devices.

| Class | Responsibility | Important methods |
|---|---|---|
| CommunicationManager | Coordinates communication | `startCommunication()`, `selectProtocol()` |
| Sender | Initiates message transmission | `sendMessage()`, `sendData()` |
| Receiver | Handles incoming data | `receivePacket()`, `deliverMessage()` |
| Message | Stores original application data | `getContent()`, `getSize()` |
| PortManager | Manages application port information | `registerPort()`, `findApplication()` |

**Example:**

When PC1 sends a message to PC3, `CommunicationManager` coordinates the process. `Sender` prepares the outgoing data, while `Receiver` handles the incoming data.

## Module 3: Packet Management

This module handles the structure and transformation of data as it travels through network layers.

| Class | Responsibility | Important methods |
|---|---|---|
| Packet | Represents a general packet | `getSize()`, `displayPacket()` |
| Segment | Represents transport-layer data | `setSequenceNumber()`, `getPayload()` |
| IPDatagram | Represents a network-layer datagram | `setSourceIP()`, `setDestinationIP()` |
| Frame | Represents data-link-layer transmission data | `addHeader()`, `addTrailer()` |
| PacketHeader | Stores packet header information | `setHeader()`, `displayHeader()` |
| PacketManager | Coordinates packet operations | `segmentData()`, `reassembleData()` |

The packet module should preserve the relationship between the original message and its segments so that the receiver can reconstruct the original data.

## Module 4: Protocol Management

This module simulates the behavior of communication protocols.

| Class | Responsibility | Important methods |
|---|---|---|
| Protocol | Common protocol abstraction | `send()`, `receive()` |
| TCP | Simulates reliable communication | `connect()`, `send()`, `close()` |
| UDP | Simulates connectionless communication | `sendDatagram()`, `receiveDatagram()` |
| TCPConnection | Maintains TCP connection state | `establishConnection()`, `terminateConnection()` |
| Acknowledgment | Stores acknowledgment information | `createACK()`, `processACK()` |
| SenderBuffer | Stores unacknowledged segments | `addSegment()`, `removeAcknowledged()` |
| ReceiverBuffer | Stores received segments | `storeSegment()`, `reassemble()` |
| TimerManager | Handles simulated timeout events | `startTimer()`, `stopTimer()`, `checkTimeout()` |
| SlidingWindow | Manages transmission windows | `moveWindow()`, `updateWindow()` |
| GoBackN | Implements Go-Back-N | `transmitWindow()`, `retransmitFrom()` |
| SelectiveRepeat | Implements Selective Repeat | `sendMissingSegment()`, `processIndividualACK()` |

`TCP` and `UDP` should follow a common protocol interface or abstract class. This allows `CommunicationManager` to work with either protocol without depending on its internal implementation.

## Module 5: Routing Management

This module determines how packets travel across the network.

| Class | Responsibility | Important methods |
|---|---|---|
| RoutingManager | Coordinates route selection | `findRoute()`, `updateRoutes()` |
| RoutingTable | Stores routing information | `addRoute()`, `findRoute()` |
| Route | Represents a path | `getCost()`, `displayRoute()` |
| Dijkstra | Finds shortest paths using non-negative edge weights | `findShortestPath()` |
| BellmanFord | Finds shortest paths and supports negative edge weights | `calculateRoutes()` |

The routing algorithms will use the network topology represented as a graph.

Possible route costs include:

- Link delay.
- Hop count.
- Bandwidth-based cost.
- Congestion-related cost.

## Module 6: DSA Management

This module contains custom implementations of data structures used by the simulator.

| Class | DSA concept | Application |
|---|---|---|
| CustomLinkedList | Linked List | Store connected devices or packets |
| CustomQueue | Queue | Manage outgoing packets |
| CircularQueue | Circular Queue | Manage fixed-size buffers |
| PriorityQueue | Priority Queue | Schedule high-priority packets |
| Heap | Heap | Efficient priority management |
| Graph | Graph | Represent network topology |

The objective is to implement and understand the data structures rather than simply calling Java's predefined collection implementations.

## Module 7: Intelligent Network Management

This module makes decisions based on current network conditions.

| Class | Responsibility | Important methods |
|---|---|---|
| IntelligentManager | Coordinates intelligent decisions | `analyzeNetwork()`, `recommendAction()` |
| CongestionDetector | Detects possible congestion | `checkCongestion()` |
| PacketClassifier | Classifies packets | `classifyPacket()` |
| RouteAdvisor | Recommends a suitable route | `recommendRoute()` |
| AnomalyDetector | Identifies unusual network conditions | `detectAnomaly()` |

Example:

```text
Network Metrics
      |
      v
CongestionDetector
      |
      v
Congestion Detected?
      |
      v
RouteAdvisor
      |
      v
Recommend Alternative Route
      |
      v
RoutingManager
      |
      v
Router Forwards Packet
```

The intelligent module recommends actions. The routing and network modules remain responsible for executing them.



## Module 8: Console Interface

| Class | Responsibility |
|---|---|
| Main | Application entry point |
| ConsoleMenu | Displays options and accepts user input |
| OutputManager | Displays network and simulation results |

The console interface will provide access to the different modules without mixing user-interface code with networking logic.

---

# 5. How the Classes Work Together

The following example explains the interaction between modules when PC1 sends a TCP message to PC3.

### Step 1: Create the network

The user creates devices using `Network`.

```text
Network
  |
  |-- PC1
  |-- Switch1
  |-- Router1
  |-- Router2
  |-- PC3
```

`NetworkLink` connects the devices.

### Step 2: Start communication

The user selects:

```text
Source: PC1
Destination: PC3
Protocol: TCP
Message: Hello Network
```

`CommunicationManager` starts the communication process.

### Step 3: Establish TCP connection

`TCPConnection` performs the three-way handshake.

```text
SYN
SYN-ACK
ACK
```

### Step 4: Create and segment data

`PacketManager` divides the message into smaller segments.

`TCP` assigns sequence numbers and prepares the segments for transmission.

### Step 5: Store segments

`SenderBuffer` stores segments that have not yet been acknowledged.

`SlidingWindow` controls how many segments can be transmitted without waiting for individual acknowledgments.

### Step 6: Determine the route

`RoutingManager` requests a suitable route.

`Dijkstra` or another selected algorithm calculates the path.

### Step 7: Forward packets

The source device passes data to the network. Switches and routers process and forward the relevant frames and packets.

### Step 8: Simulate transmission conditions

`SimulationEngine` manages simulated events.

The simulator can introduce:

- Transmission delay.
- Packet loss.
- Link failure.
- Queue congestion.
- Timeout events.

### Step 9: Process acknowledgments

The receiver processes incoming segments and sends acknowledgments.

`TimerManager` checks for timeouts. TCP retransmits data when the selected reliability mechanism requires it.

### Step 10: Reassemble the message

`ReceiverBuffer` stores the received segments.

`PacketManager` reassembles the original message.

### Step 11: Display results

`NetworkMetrics` calculates delivery statistics.

`OutputManager` displays the final results.

---

# 6. How the Team Will Work: Module-Wise Development

Development should be divided into modules rather than allowing every team member to edit the same classes independently.

Each module should have defined responsibilities, input/output expectations, and interfaces.

| Work package | Main responsibility | Suggested deliverable |
|---|---|---|
| Network module | Devices, links, topology | Working network creation |
| Communication module | Sender, receiver, messages | Basic device-to-device communication |
| Packet module | Segmentation and headers | Packet creation and reassembly |
| Protocol module | TCP, UDP, reliability | Protocol simulation |
| Routing module | Graph and routing algorithms | Working route selection |
| DSA module | Custom data structures | Tested data structures |
| Intelligence module | Rule-based decisions | Congestion and route recommendations |
| ML module | Dataset and ML algorithms | Training and prediction |
| Simulation/UI module | Simulation coordination and CLI | Integrated application |

The final allocation of work can depend on the number of team members and their experience.

## Recommended Development Phases

### Phase 1: Foundation

- Create the Java project.
- Define package structure.
- Create common classes and interfaces.
- Implement custom data structures.
- Establish naming conventions and coding standards.

### Phase 2: Network Creation

- Create devices.
- Create network links.
- Connect devices.
- Represent topology using a graph.
- Display the network.

### Phase 3: Basic Communication

- Create messages.
- Implement sender and receiver.
- Implement basic packet creation.
- Establish source and destination communication.
- Test basic message delivery.

### Phase 4: Protocol Implementation

- Implement UDP.
- Implement TCP.
- Add the three-way handshake.
- Implement segmentation.
- Add sequence and acknowledgment numbers.
- Implement sender and receiver buffers.
- Add reliable data transfer algorithms.

### Phase 5: Routing and Simulation

- Implement BFS and DFS.
- Implement Dijkstra.
- Add routing tables.
- Simulate packet forwarding.
- Add delay, loss, and link failure.
- Implement timeout and retransmission events.

### Phase 6: Intelligent System

- Collect network metrics.
- Implement rule-based congestion detection.
- Add packet classification.
- Recommend alternative routes.
- Implement network anomaly detection.



### Phase 7: Final Integration

- Integrate all modules.
- Test communication between different devices.
- Test different network topologies.
- Verify routing and packet delivery.
- Display network performance statistics.
- Improve the CLI experience.

---



### System Work Flow

Use a shared GitHub repository with a `main` branch and separate feature branches.

=====================================
       NETWORK SIMULATOR
=====================================

1. Create Network
2. Add Device
3. Connect Devices
4. Display Network
5. Start Communication
6. Select Protocol
7. Configure Routing
8. Run Simulation
9. View Network Statistics
10. Intelligent Network Analysis
11. Machine Learning Predictions
12. Exit

Select Option: 5

Source Device: PC1
Destination Device: PC3

Enter Message: Hello Network

Select Protocol:
1. TCP
2. UDP

Select: 1

Establishing TCP Connection...

SYN Sent
SYN-ACK Received
ACK Sent

Connection Established!

Segmenting Message...

Calculating Route...

Forwarding Packets...

Receiving Acknowledgments...

Reassembling Message...

=====================================
       COMMUNICATION RESULTS
=====================================

Original Message: Hello Network
Source: PC1
Destination: PC3
Protocol: TCP
Packets Sent: [Calculated]
Packets Received: [Calculated]
Packets Lost: [Calculated]
Retransmissions: [Calculated]
Average Delay: [Calculated]
Delivery Status: [Calculated]

=====================================
```

*The output values above are placeholders for values calculated by the actual simulator.*

---

# 9. Technology Stack

| Technology | Purpose |
|---|---|
| Java | Core development language |
| OOP | Modular software architecture |
| DSA | Network data management |
| Graph Algorithms | Network topology and routing |
| TCP/UDP Concepts | Communication simulation |
| Basic Machine Learning | Network prediction and classification |
| Git | Version control |
| GitHub | Team collaboration |
| VS Code / IntelliJ IDEA | Development environment |

The initial simulator will be CLI-based and will not require external machine learning libraries.

---

# 10. Future Enhancements

After the core simulator is stable, possible enhancements include:

- Graphical network topology editor.
- Interactive packet animation.
- More advanced routing protocols.
- Real socket-based communication.
- Advanced congestion control.
- Reinforcement Learning for adaptive routing.
- More advanced anomaly detection.
- Network configuration dashboard.
- Simulation result visualization.

---

# 11. Project Scope

The project is planned in stages.

| Component | Initial scope |
|---|---|
| Network topology | Device creation and connections |
| Communication | Simulated sender and receiver |
| Protocols | TCP and UDP |
| Packet management | Headers, segmentation and reassembly |
| Reliable transmission | ACKs, buffers, timers and retransmission |
| Routing | Graph-based path selection |
| DSA | Custom data structures |
| Intelligent system | Rule-based network decisions |
| Machine Learning | Basic ML algorithms from scratch |
| Neural Networks | Future enhancement |
| GUI | Future enhancement |

**Important:** This repository describes the intended architecture and development plan. Features should only be marked as implemented after they have been developed and tested.

---

# 12. Final Vision

The long-term goal is to build an educational and intelligent network simulation platform that combines the fundamentals of computer networking with the practical implementation of data structures, algorithms, and machine learning.

Instead of simply showing how packets move through a network, the simulator aims to explain and demonstrate the internal processes behind communication, routing, reliability, congestion management, and intelligent decision-making.

The project will be developed incrementally, beginning with a functional Java CLI simulator and gradually evolving into a more advanced network simulation platform.