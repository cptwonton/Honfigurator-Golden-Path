# Security Groups Configuration

When setting up your EC2 instance for hosting Project Kongor Heroes of Newerth servers, it's essential to configure the security groups to allow traffic on specific ports. Here's a breakdown of the required ports and protocols:

1. **Port 10000 (UDP)**
   - Protocol: UDP
   - Source: 0.0.0.0/0 (Anywhere)

2. **Ports 10061-10077 (UDP)**
   - Protocol: UDP
   - Source: 0.0.0.0/0 (Anywhere)
   - Note: Assumes HonFigurator may spin up 16 servers.

3. **Ports 10001-10017 (UDP)**
   - Protocol: UDP
   - Source: 0.0.0.0/0 (Anywhere)
   - Note: Assumes HonFigurator may spin up 16 servers.

4. **Port 5000 (TCP)**
   - Protocol: TCP
   - Source: 0.0.0.0/0 (Anywhere)

5. **Port 3389 (TCP)**
   - Protocol: TCP
   - Source: 0.0.0.0/0 (Anywhere)

6. **Port 1134 (TCP)**
   - Protocol: TCP
   - Source: 0.0.0.0/0 (Anywhere)

7. **Port 22 (TCP)**
   - Protocol: TCP
   - Source: 0.0.0.0/0 (Anywhere)
   - Note: Enabled by default and allows SSH access to your instance. Consider restricting this if security concerns arise, though it's generally not necessary.

Remember, allowing traffic from `0.0.0.0/0` means the port is open to the entire internet. Adjust these settings based on your security requirements. Happy securing!
