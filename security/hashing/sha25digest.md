# SHA-256 Digest

Digest is a one way hash for an input message.
SHA-256 stands for **Secure Hash Algorithm 256-bit**. SHA-256 Digest generates a fixed width digest for any and every input. The fixed width is 256 bits = 32 bytes. A small change in the input, generates a completely different output (avalanche effect).

A **digest** is a fixed-size hash computed from arbitrary input data. It’s used to verify **integrity**, **authenticate contents**, and support **cryptographic protocols**.
## Properties of Cryptographic Hash Functions

- **Deterministic**: Same input → same hash
- **Fixed length output**: SHA-256 always returns 256 bits (32 bytes)
- **Fast computation** (though cryptographic hashes are slower than non cryptographic algorithms like Murmur3 Hash or FNV)
- **Pre-image resistance**: Given a hash, hard to find input
- **Second pre-image resistance**: Hard to find another input with same hash
- **Collision resistance**: Hard to find two different inputs with same hash
- **Avalanche effect**: Small input change → major hash change

## Algorithm Steps:

1. Pad `1 bit` to the end of the message.
2. Pad `x number of 0` to the end of the message. Post padding, the length of the message should be congruent to `448 % 512`. Since SHA-256 processes chunks of `512 bits (64 bytes)`, the overall length must be mod 512.
3. The 1 and 0 padding is done in a way, which leaves just 64 bit space for overall length to become mod 512.
4. Append the message length as `64-bit big-endian value`. 
5. Iterate over the buffer, in 512 bit chunks (64 bytes).
	1. Load the first 16 bytes as big endian.
	2. Load the next 48 bytes and do the rotations as mentioned in the [wiki](https://en.wikipedia.org/wiki/SHA-2#Pseudocode)
	3. Load up the 8 magical constants used for hashing.
	4. Start with the compression of the 64 byte chunk. Do some pure math and bit manipulation magic as mentioned in wiki, you get `s1, ch, s0, maj`
	5. Add the compressed chunk to current hash value
6. The overall hash/digest is the concat of the 8 hashes.

Implementation of the same can be found in [SHA265Digest.java](https://github.com/priyakdey/sigil/blob/main/core/src/main/java/com/priyakdey/sigil/core/crypto/digest/SHA256Digest.java)

## References
- https://www.rfc-editor.org/rfc/rfc6234.html
- https://csrc.nist.gov/pubs/fips/180-4/upd1/final
- https://en.wikipedia.org/wiki/SHA-2/