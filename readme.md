## Aqua
Aqua is a new-gen language for distributed systems.

Aqua programs are executed on many peers, sequentially
or in parallel, forming a single-use coordination network.

Aqua's runtime is heterogeneous: it includes browsers, servers, devices, all involved in solving a single task.
Therefore, Aqua scripts are compiled into several targets at once, with AIR and Typescript as a default.

## aqua-lib

API of the protocol-level functions in the Fluence Network.

This API is available on all peers powered by Fluence nodes, and a part of the API is available on JS/TS-based (browsers, NodeJS) peers.

### Documentation
See [Aqua Book](https://fluence.dev/aqua-book/libraries/aqua-dht).

### How to use it in Aqua

Add `@fluencelabs/aqua-lib` to your package.json dependencies, and then in your Aqua script, import and use it:
```haskell
import "@fluencelabs/aqua-lib"

-- gather Peer.identify from all nodes in the neighbourhood
func getPeersInfo() -> []Info:
    infos: *Info
    nodes <- Kademlia.neighborhood(%init_peer_id%, nil, nil)
    for node in nodes:
        on node:
            infos <- Peer.identify()
    <- infos
```

