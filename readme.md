Personal Firewall Using Python

A lightweight Python-based personal firewall that monitors network traffic, filters packets based on customizable rules, logs suspicious activity, and optionally enforces system-level blocking using iptables. Designed as an internship project to demonstrate knowledge of networking, packet inspection, rule engines, and security automation.

📌 Features

a. Packet sniffing using Scapy (incoming & outgoing traffic)

b. Rule-based filtering (IP, port, protocol, direction)

c. Actions: ALLOW, BLOCK, LOG, IPTABLES_BLOCK

d. JSON-based rule storage with dynamic loading

e. Logging of suspicious packets with timestamps

f. CLI for rule management & starting/stopping firewall

g. Optional Tkinter GUI for live monitoring

h. Optional integration with iptables for kernel-level blocking

personal-firewall/
├── sniffer.py            # Scapy-based packet sniffer
├── rule_engine.py        # Rule matching logic
├── enforcer.py           # iptables wrapper for strong blocking
├── cli.py                # CLI to manage rules and run firewall
├── gui.py                # Optional Tkinter GUI
├── rules.json            # Rule configuration
├── logs/                 # Packet + action logs
└── README.md


🔧 Prerequisites

a. System

b. Linux OS (Ubuntu/Debian recommended)

c. Root or sudo privileges

Install Dependencies

a. sudo apt update
b. sudo apt install python3 python3-venv python3-pip iptables
c. python3 -m venv venv
d. source venv/bin/activate
e. pip install scapy rich watchdog

🚀 Getting Started
1. Clone the project
  git clone <your-repo-url>
cd personal-firewall
 
2. Load the virtual environment
   source venv/bin/activate

3. Run the sniffer
   sudo python3 sniffer.py

4. Start the firewall
   sudo python3 cli.py start

5. View rules
   python3 cli.py rules list

6. Add a rule
   python3 cli.py rules add --file new_rule.json

📝 Example Rule (rules.json)
[
  {
    "id": "r1",    
    "action": "BLOCK",
    "direction": "INBOUND",
    "proto": "TCP",
    "src_ip": "0.0.0.0/0",
    "dst_ip": "192.168.1.10",
    "dst_port": 22,
    "comment": "Block SSH attempts"
  }
]

📁 Logs

Logs are saved in logs/ with metadata:
{
  "timestamp": "2025-11-23T12:00:00Z",
  "packet": {
    "src": "1.2.3.4",
    "dst": "192.168.1.10",
    "proto": "TCP",
    "dport": 22
  },
  "rule_matched": "r1",
  "action": "BLOCK",
  "method": "iptables"
}

🖥 Optional GUI

Start the GUI:
🖥 Optional GUI
   python3 gui.py

Features:

a. Live packet feed

b. Rule viewer/editor

c. Apply/remove iptables rules

d. Toggle firewall on/off

🔬 Testing
Generate test traffic:
nc -l 8080        # listen
nc <host-ip> 8080 # send packet to test blocking

Verify iptables blocking
 sudo iptables -L -n --line-numbers

⚠️ Safety Warnings

a. Do NOT run on networks you do not own.

b. Misconfigured iptables can block SSH and lock you out.

c. Always keep a "safe mode" / undo script ready.

📌 Future Enhancements

1.GeoIP blocking

2. Real-time alerts via email/Slack

3. Web-based dashboard

4. Machine-learning–based anomaly detection

5. Scheduled rules & rate-limiting

   👨‍💻 Author
   
MANOJ KUMAR B R

Cybersecurity Intern • Python & Networking Enthusiast
