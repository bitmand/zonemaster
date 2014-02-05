## DELEGATION05: Test whether the referrals response at the authoritative and additional section fit into 512 byte UDP packet

### Test case identifier
**DELEGATION05:** Test whether the referrals response at the authoritative and additional section fit into 512 byte UDP packet

### Objective
The Domain Name System defaults to using UDP for queries and replies with a DNS payload limit of 512 bytes.  Larger replies cause an initial truncation indication leading to a subsequent handling via TCP with substantially higher overhead.  EDNS0 is used to permits larger UDP responses thus reducing the need for use of TCP.

But [IANA](https://www.iana.org/help/nameserver-requirements) still maintai
ns that referrals from the parent zonne name servers must fit into a non-ED
NS0 UDP DNS packet. Hence this test is done.

In this test, the authoritaitve and additional section of the referral response from the domain must fit into a 512 byte UDP packet.

### Inputs
1. The FQDN of the authoritative name servers
2. All IPv4 and IPv6 addresses for authoritative name servers

### Ordered description of steps to be taken to execute the test case
1. An empty DNS answer packet is generated.
2. All the data from the input is added to the packet.
3. If the size of the packet is more than 512 bytes, then the test fails

### Outcome(s)
If the created packet fits into 512 byte UDP packet, then the test succeeds

### Special procedural requirements
None

### Intercase dependencies
None