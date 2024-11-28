# Network Topology to Mermaid JS diagram
Contributed by [@spoofnet](https://github.com/spoofnet)

## Overview
Creates a [Mermaid JS](https://mermaid.js.org/syntax/architecture.html) syntax text diagram of a given Network Topology that can be easily embedded (and automatically rendered as a visual diagram) into a [Microsoft Loop](https://loop.microsoft.com) page, GitHub write-up or similar that is capable of rendering [Mermaid diagrams](https://mermaid.js.org). Aims to assist in Network Documentation on Wiki and Wiki-like knowledge platforms.

## AI Prompt
```text
Create a Mermaid Architecture diagram of the following network:

| Device | Type | Icon |
| ------- | ------ | ---- |
| LDN2-RTR-001 | Router | Cisco Router |
| MAN1-SWT-009 | Layer 3 Switch | Juniper Switch | 
| EDI9-FWL-006 | Firewall | Palo Alto Firewall #1 |
| EDI9-FWL-007 | Firewall | Palo Alto Firewall #2 |

The links are as follows:

| A-End Device | A-End Port | B-End Device | B-End Port | Link Description |
| --------------- | ----------- | --------------- | ------------ | ------------------ |
| EDI9-FWL-006 | eth1 | EDI9-FWL-007 | eth2 | Palo HA Subnet |
| EDI9-FWL-006 | eth2 | LDN2-RTR-001 | eth1 | WAN Circuit ICUK123456 |
| EDI9-FWL-007 | eth2 | LDN2-RTR-001 | eth2 | WAN Circuit ICUK654321 |

Respond only with the Mermaid syntax response and no other explanations.
```

## Example AI Response
```javascript
graph TD
    LDN2-RTR-001[Router: LDN2-RTR-001]
    MAN1-SWT-009[Layer 3 Switch: MAN1-SWT-009]
    EDI9-FWL-006[Firewall: EDI9-FWL-006]
    EDI9-FWL-007[Firewall: EDI9-FWL-007]

    EDI9-FWL-006 -- eth1 --> EDI9-FWL-007
    EDI9-FWL-006 -- eth2 --> LDN2-RTR-001
    EDI9-FWL-007 -- eth2 --> LDN2-RTR-001
```

## Usage Notes
* Works best in OpenAI Chat GPT-4o mini or Copilot
* Replace the example Network devices with your applicable environment
* Replace the example Link Descriptions with your applicable environment