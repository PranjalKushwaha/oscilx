---
layout: post
# icon: fas fa-solid fa-microchip
order: 1
toc: true
---

## Introduction

This writeup introduces the wireless mesh protocol stack developed by Oscilx Labs from a technical perspective. Certain concepts and explanations are intentionally kept vague. Detailed technical white papers can be obtained by [contacting us directly]({{ site.baseurl }}/contact){:target="_blank"}.

## Problems with current solutions

Current market solutions for deploying wireless mesh networks suffer from one major drawback, the routing nodes consume a significant amount of power due to the design of these protocols that require them to be powered on at all times to receive data. This means that in most cases only the last edge node can be battery powered for a long time restricting the area where the network can be successfully deployed.

Newer solutions like BLE Mesh, IEEE 802.15.4e and WirelessHART have been proposed to counter this and they are discussed later.

## Working principle

The end goal for the protocol is simple, reduce energy consumption which in turn translates to reducing the duty cycle of the radio. On analysis of the aforementioned mesh technologies, it is evident that routing nodes keep their radios on in receive mode even if they are not actively using it. This is because there is uncertainty in the transmission time of each node. Our solution was to create a time scheduling algorithm to synchronise the radio activity in the network to obtain the lowest duty cycle. This along with improvements in other aspects of networking allow us to achieve some of the [lowest power consumption numbers for routing nodes]({{site.baseurl}}/benchmark){:target="_blank"}.

## Improvements

The novel protocol comes with significant improvements over the competition in the areas of:

- Link Layer:

  1. Network time independent slot scheduling: better slot alignment with nodes at different network depths.
  2. Adaptive clock drift correction: allows operation with inaccurate clock sources.
  3. Efficient link protocol: Works with overhead as low as 20bytes per 16 data packets.
  4. Timeout negotiation: A dynamic slot timeout negotiation based on the number of pending packets.
  5. Minimal PHY requirements: Requires the physical layer to support only bare-bones functionality

- Network Layer:
  1. Cheaper downstream communication: Low overhead for routing from root to network nodes.
  2. Redundant paths: Ensures reliability in case of link failures.
  3. Table-less routing: An innovative routing protocol using an algorithm set for packet routing leads to no need for routing tables and other structures saving memory 

These along with other major innovations throughout the network stack allow extreme energy efficiency with reliability.
Also due to using easy-to-compute algorithms and state machines, the protocol can be run on relatively low-end processor cores. Also due to code optimisation and overlapping data paths the entire networking stack can fit in <20kB of flash and takes <2kB of SRAM, with the rest left for the user application or reserved by larger network buffers. 
This allows the usage of much cheaper hardware for deploying the network giving it a serious edge over the competition.

## Comparison with competing standards

| Paremeter             | Oscilx          | WirelessHART      | IEEE 802.15.4e  | BLE Mesh         |
| --------------------- | --------------- | ----------------- | --------------- | ---------------- |
| Frequency Band        | 2.4Ghz, sub-Ghz | 2.4GHz            | 2.4Ghz, sub-Ghz | 2.4GHz           |
| Channel Access        | Channel Hopping | TSMP              | TSCH            | FHSS             |
| Slot Scheduling       | Distributed     | Centralised       | Distributed     | Distributed      |
| Routing               | Proprietary     | Centralised Graph | RPL             | Network Flodding |
| Group Acknoledgements | Yes             | Yes               | Yes             | No               |
| Physical layer spec   | Minimal         | 802.15.4          | 802.15.4        | BLE              |

