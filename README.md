# Andrew-Secure-RPC

The Andrew secure RPC allows two parties, A and B (usually a client and a server), who already share a key Kab, to agree upon a new key K'ab. The protocol also performs an authentication handshake. There are four messages in the protocol exchange. The first three, A and B perform a handshake using a shared secret Kab. In the final message, B sends a new key K'ab to A. The protocol can be summarised as follows. Note that nonce Na is chosen by A and nonces N'b, Nb are chosen by B.

1. A → B : {Na}Kab
2. B → A : {Na + 1, Nb}Kab
3. A → B : {Nb + 1}Kab
4. B → A : {K'ab, N'b}Kab

Problems with the protocol: 
1. That is, there is nothing that can guarantee that K'ab is fresh.
2. An intruder could record the second message and substitute it in place of the fourth. The result is that A would accept Na + 1 as a new key. However, for this attack to be successful, it depends
on the property of the nonce Na, i.e., whether or not the nonce is predictable.
