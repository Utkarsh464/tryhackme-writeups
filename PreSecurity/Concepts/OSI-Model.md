# OSI Model

## Definition
The Open Systems Interconnection (OSI) model is a conceptual framework with **7 layers** that standardizes how network protocols communicate: Physical (1), Data Link (2), Network (3), Transport (4), Session (5), Presentation (6), Application (7). Each layer provides services to the layer above and receives services from the layer below.

## Why It Matters
The OSI model helps you isolate problems, understand protocol interactions, and design interoperable systems. Security professionals use it to identify where attacks occur (e.g., ARP spoofing at Layer 2, SYN floods at Layer 4) and where to place defenses (e.g., encryption at Layer 6, firewalls at Layers 3-4).

## Where It Appears in the Path
- Network Fundamentals

## Prerequisites
- Basic networking concepts

## Key Points
- PDU names: bit (L1), frame (L2), packet (L3), segment (L4), data (L5-7)
- Encapsulation: each layer adds its own header
- Mnemonic: "Please Do Not Throw Sausage Pizza Away"
- Security controls exist at every layer

## Common Interview Questions
1. Which layer does IP operate at?
**Answer:** Layer 3 (Network).
2. Which layer does TCP operate at?
**Answer:** Layer 4 (Transport).
3. What is encapsulation?
**Answer:** Each layer adds a header (and sometimes trailer) to data as it travels down the stack.

## Further Reading
- ISO/IEC 7498-1
- RFC 1122