# PRE INSTALLATION:
  Ensure you have Python installed. Install Scapy,a powerful Python library for interacting with network packets:
  
  ![WhatsApp Image 2024-06-25 at 12 55 54 PM](https://github.com/anushka-2005/PRODIGY_CS_05/assets/173171188/0c99ba0c-3f46-488a-b3c9-2b5a7162d568)
  
  And before performing your coding you must install Wimpcp or npcap.
# WIMPCAP INSTALLATION:
  ![WhatsApp Image 2024-06-25 at 1 01 49 PM](https://github.com/anushka-2005/PRODIGY_CS_05/assets/173171188/978a6877-128a-48a0-8ed3-1ea00c0eb48a)
# NPCAP INSTALLATION:
  ![WhatsApp Image 2024-06-25 at 1 03 27 PM](https://github.com/anushka-2005/PRODIGY_CS_05/assets/173171188/ec0b447f-d549-48d9-85df-649e1911c98a)
# CODE:
  import scapy.all as scapy

  def packet_callback(packet):
  
     if packet.haslayer(scapy.IP):
          src_ip = packet[scapy.IP].src
          dst_ip = packet[scapy.IP].dst
          protocol = packet[scapy.IP].proto

          print(f"Source IP: {src_ip} | Destination IP: {dst_ip} | Protocol: {protocol}")

          if packet.haslayer(scapy.TCP):
              try:
                  payload = packet[scapy.Raw].load
                  decoded_payload = payload.decode('utf-8', 'ignore')
                  print(f"TCP Payload")
              except (IndexError, UnicodeDecodeError):
                  print("Unable to decode TCP payload.")

          elif packet.haslayer(scapy.UDP):
              try:
                  payload = packet[scapy.Raw].load
                  decoded_payload = payload.decode('utf-8', 'ignore')
                  print(f"UDP Payload")
              except (IndexError, UnicodeDecodeError):
                  print("Unable to decode UDP payload.")

  def start_sniffing():
      
      scapy.sniff(store=False, prn=packet_callback)

  start_sniffing()
