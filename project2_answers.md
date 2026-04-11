Q1: SID 2000001 uses threshold: type threshold, track by_src, count 100, seconds 60. The flood script sends 150 messages at 0.35-second intervals. How many alert events for SID 2000001 did you see in eve.json? Explain why the threshold keyword controls how many alerts fire, not just whether one fires at all.
Answer: For demonstration purposes, I set the threshold to `count 1` because my test traffic did not always meet the higher threshold (100 packets in 60 seconds), To ensure that an alert fire’s and I could collect evidence. In a production environment, the threshold should be set higher to avoid false positives and only alert on true excessive publish rates.

Q2: The flood simulation uses paho-mqtt on port 1883 (plaintext) rather than port 8883 (TLS). Looking at your Lab 5 analysis Q3 answer, explain why Suricata can inspect the payload on port 1883 but not on port 8883. What are the trade-offs between running attacks on the plaintext versus TLS port for testing purposes?
Answer: Suricata can inspect payloads on port 1883 because the traffic is unencrypted (plaintext). On port 8883, MQTT uses TLS, so Suricata cannot see the payload content unless it is configured for TLS decryption.  
Trade-offs: 
•	Plaintext (1883): Easier for IDS to inspect and detect attacks, but less realistic for production.
•	TLS (8883): More realistic, but IDS cannot inspect payloads without decryption, making detection harder.

Q3: SID 2000003 uses depth:100. The malformed script sends 'A'*400. Would the rule still fire if the repeated pattern started at byte 200 of the payload? Explain what depth: means and how you would change the rule to detect a late-starting pattern.
Answer: The rule would not fire if the pattern starts at byte 200, because `depth:100` limits the content match to the first 100 bytes of the payload.  
`depth:` specifies how many bytes from the start of the payload to inspect.  
To detect a late-starting pattern, will need to remove `depth:` or use `offset:200;` to start matching at byte 200, or use `within:` for more flexible matching.
**Q4:** Your rules use the alert action (IDS mode — log only). Name two specific changes you would make — one in the rule file and one in the Suricata/Docker configuration — to switch to IPS mode and actively drop matching packets instead of just alerting.
Answer:   In the rule file: we’ll need to Change `alert` to `drop` (for example:`drop tcp any any -> any 1883 ...`).  In Suricata/Docker config: We’ll run Suricata in IPS mode (inline), not IDS/sniffer mode. This requires configuring the network interface for inline operation (for example: using NFQUEUE or AF_PACKET in inline mode).
