# Using Nmap to adhere to compliance and enhance the Security Posture

# Scenario for the project
I am a junior cybersecurity analyst tasked with securing a standalone Windows computer in a corporate environment. During your initial assessment using Nmap from my laptop, I discovered that ports 135, 139, and 445 were open on the Windows computer, posing potential security risks. Following best practices and company policies, I implemented firewall rules to restrict inbound traffic on these ports specifically to the domain profile, while blocking access from public and private profiles.

Policy: 
- According to the Policy, ports 135,139,445 should not be accessible through the public or private profiles and it should be accessible to the domain profile so that devices that are part of the Active Directory domain. This ensures that domain-joined computers and servers can communicate with the necessary services on the specified ports.

# Nmap to find open ports 

Here we use Nmap to find potential open ports on the first 1000 ports for this system. We can see 3 ports are open. We used -Pn to avoid the ping step of the Nmap scan as it was blocking the ping probes, thus allowing us to go directly to the scan. 

![Screenshot 2024-06-17 at 1 32 52 PM](https://github.com/SteveSunny46/Using-Nmap-to-secure-a-comptuer-/assets/171859383/100d0dec-9696-4d65-bc04-5517296c7ec8)

# Following best practices and company policies 

To follow best practices and company policies we will implement firewall rules to restrict inbound traffic on these ports to the domain profile while blocking the public and private profiles. 

![Screenshot 2024-06-17 at 1 33 09 PM](https://github.com/SteveSunny46/Using-Nmap-to-secure-a-comptuer-/assets/171859383/eed04316-a7e3-4171-9061-29c8fe3a0020)

![Screenshot 2024-06-17 at 1 34 56 PM](https://github.com/SteveSunny46/Using-Nmap-to-secure-a-comptuer-/assets/171859383/0012018f-3866-4a10-b094-4a463ad1805a)

![Screenshot 2024-06-17 at 1 35 04 PM](https://github.com/SteveSunny46/Using-Nmap-to-secure-a-comptuer-/assets/171859383/b356b853-a0dd-4d0f-9bf6-0f2294880654)


# Confirm the ports are now closed 

To confirm if external sources can perform Nmap scans on this computer and see if these ports are still open we conduct another Nmap scan. This allows us to see that the firewall rule we set did work. 


![Screenshot 2024-06-17 at 1 48 40 PM](https://github.com/SteveSunny46/Using-Nmap-to-secure-a-comptuer-/assets/171859383/e4572d5a-353e-44bd-ae1f-237a3dfe4990)

Note: Ports showing as "filtered" mean that Nmap could not determine whether they are open or closed because it did not receive any response (neither open nor closed). This often occurs when ports are blocked by a firewall or another network device.

# Conclusion 
After implementing firewall rules to block inbound traffic on ports 135, 139, and 445 for public and private profiles, and allowing access only from devices within the domain profile, Nmap scans from external sources (like your laptop) should no longer detect these ports as open. This ensures that the Windows computer is not vulnerable to external reconnaissance attempts, enhancing its security posture against potential threats.
