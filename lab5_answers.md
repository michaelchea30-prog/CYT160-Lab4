11. Analysis Questions

Answer in lab5_answers.md committed to GitHub. One or two paragraphs per question.
Q1: Open both pcaps with tcpdump -r <file> -nn -A and compare the output. List three specific
things that are visible in the plaintext capture but hidden in the TLS capture. What does this
mean for an attacker who can intercept network traffic between the Pi and the broker?

Answer: Because port 1883 is used for plain, unencrypted MQTT traffic. It is easier for an attacker or anyone to access the network. But using port 8883 on the network will encrypt the data in transit, protecting it from eavesdropping and tampering. Making only user with the correct certificates can connect when mutual TLS is enabled.


Q2: Your mosquitto.conf sets require_certificate true. What does this mean for a client that tries
to connect without a certificate? Test it: run mosquitto_sub -h <VM_IP> -p 8883 -t '#' from a
terminal that does NOT provide --cafile, --cert, and --key flags. What error message do you get?
Why is this a security improvement over allow_anonymous true?

Answer: In the plaintext pcap (port 1883), you can see the MQTT message payloads are visible and able to read, but with the TLS pcap (port 8883), the payload is encrypted and the actual message content is not visible, demonstrating the confidentiality provided by TLS.


Q3: Suricata is monitoring port 1883 (plaintext). It cannot read the encrypted payload on port
8883 without the TLS session keys. Given this limitation, what can Suricata still usefully observe about TLS traffic — and how would you use that to detect a threat on port 8883? This is relevant to the rules you will write in Project 2.

Answer: The TLS session keys are private keys which are sensitive credentials that prove the identity of the server or client.  it cannot be exposed publicly, and if the key is accidentally committed, it should be considered compromised and must be regenerated immediately.

