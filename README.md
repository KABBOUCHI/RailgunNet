**RailgunNet: A Client/Server Network State-Synchronization Layer for Games**

Alexander Shoulson, Ph.D. - http://ashoulson.com

---

Based loosely on the [Quake 3](https://github.com/id-Software/Quake-III-Arena) and [Valve/Source](https://developer.valvesoftware.com/wiki/Source_Multiplayer_Networking) networking models.

---

Supported Networking Tasks:
- Compact bit-packing of serialized entity data
- Delta-compression for entity data
- Network clock (frame number) sync
- Smoothing and interpolation support
- Client-side prediction support
- Reliable global events
- Scoping and packet size/QoS enforcement

To-Do:
- Unreliable entity/controller events
- Lag compensation support
- ...and a lot more

Wishlist:
- Code generation for new synced object states

Not Supported:
- Transport-layer network packet I/O

Primary Design Features of Railgun:
- **Transport-Agnostic.** Railgun is not tied to the transport layer used for transmitting data over the internet. As long as a simple interface is upheld (essentially just sending/receiving unreliable byte[] arrays), Railgun can work with a number of network libraries.
- **Low-Bandwidth.** Railgun uses bit-packing and delta compression to keep bandwidth use at a minimum. Additional compression techniques (like Quake's Huffman Encoding) are also under consideration.
- **Simplicity.** Railgun is designed to be simple to read and debug. This library offers as minimal a feature set as possible to keep the total source small and readable. While Railgun could certainly benefit from features like code generation for custom object serialization, code simplicity takes a higher priority.

Caveats:
- Railgun is *not* a networking library. It provides no explicit support for UDP or TCP data transfer. Railgun is designed to sit right above such a library and use it to transmit and receive data that Railgun then interprets. For a simple UDP library that serves as a perfect companion to Railgun, see [MiniUDP](https://github.com/ashoulson/MiniUDP).
