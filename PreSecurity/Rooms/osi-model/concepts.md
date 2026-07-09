# Concepts: OSI Model

## 1. The OSI Model
The Open Systems Interconnection model is a 7-layer conceptual framework developed by ISO. It divides network communication into abstraction layers, each with specific functions. Data flows down the layers on the sender side and up on the receiver side.

## 2. Layer 1 - Physical
Transmits raw bits over a physical medium. Defines hardware specifications: cable types (Cat5, Cat6, fiber), connectors (RJ45, LC), voltages, and signaling. Devices: hubs, repeaters, modems, network cables. No addressing occurs at this layer.

## 3. Layer 2 - Data Link
Packages data into frames with MAC addresses. Handles error detection (CRC), flow control, and media access control. Divided into LLC (Logical Link Control) and MAC sublayers. Devices: switches, bridges. Protocol: Ethernet (IEEE 802.3).

## 4. Layer 3 - Network
Responsible for logical addressing (IP addresses) and routing packets across networks. Determines the best path using routing protocols (OSPF, BGP). Fragments packets if they exceed MTU. Device: router. Protocol: IP (Internet Protocol).

## 5. Layer 4 - Transport
Provides end-to-end communication between applications. TCP offers reliable, connection-oriented delivery with sequencing and retransmission. UDP offers fast, connectionless delivery without guarantees. Uses port numbers to differentiate services.

## 6. Layer 5 - Session
Manages sessions (dialogues) between applications. Establishes, maintains, and terminates connections. Handles checkpointing and recovery. Protocols include NetBIOS and RPC.

## 7. Layer 6 - Presentation
Translates between application data formats and network formats. Handles encryption/decryption (TLS/SSL), compression, and character encoding (ASCII, Unicode, EBCDIC).

## 8. Layer 7 - Application
The closest layer to the end user. Provides network services directly to applications. Protocols include HTTP, HTTPS, FTP, SMTP, DNS, and DHCP. This is where web browsers, email clients, and file transfer applications operate.
