# Monas

> **A decentralized protocol for intentional data connection — where users decide what to share, with whom, and when.**

Monas is adecentralized protocol and its implementation that gives users true sovereignty over their data.  
Rather than storing or managing data on behalf of users, Monas defines how content behaves: how it is encrypted, versioned, and kept consistent across a distributed network — without trusting any single node.

End users interact with Monas through applications built on top of the protocol. Everything is open. Explore freely 👋

---

## Why Monas?

Three fundamental problems exist in today's data infrastructure:

| Problem | Description |
|---|---|
| **Authenticity** | Tampering detection and history verification are insufficient; data integrity cannot be trusted |
| **Consistency** | Data fragments across services and environments, creating contradictions with no resolution |
| **True self-sovereignty** | Self-sovereign identity efforts exist, but platform dependency persists — real user control remains elusive |

Monas addresses all three through a protocol that guarantees **state consistency and content authenticity**, while enabling users to intentionally connect their data across applications and services.

---

## How It Works

**The key principle:** `state-node` manages state — but never sees plaintext. Actual content is encrypted client-side and stored separately. The node only knows the Content ID (CID), version history, and access policies — never the content itself.

Content is addressed by CID (a SHA-256-based identifier). Because CIDs are derived from content hashes, they are storage-agnostic and tamper-evident — any modification changes the CID.

Each piece of content has its own **Content Network**: a P2P cluster of state-nodes selected by XOR distance (Kademlia DHT), ensuring no single party can control which nodes are chosen. CRDT-based state management keeps the network consistent even under Byzantine conditions.

---

## Repositories

### [`monas`](https://github.com/Monas-project/monas)
The core protocol implementation. Contains the client-side components for key management (`monas-account`), content encryption and sharing (`monas-content`), distributed state management (`monas-state-node`), and the storage abstraction layer (`monas-filesync`).

### [`crsl-lib`](https://github.com/Monas-project/crsl-lib)
A CID-native DAG CRDT library. Enables conflict-free distributed state synchronization across state-nodes, where every operation is identified by its CID. Designed to be Byzantine-fault tolerant and extensible toward future capabilities like FHE-based encrypted merging.


---

## What's Next

Monas currently defines the behavior of individual content units — encryption, storage, and Content Network management. The next layer is **Space**: a user-controlled data domain that allows grouping content, delegating access, and connecting with external applications at a granular level.

This will be realized through an encrypted logical filesystem based on an evolution of Cryptree — with an open protocol specification so anyone can build their own implementation.

