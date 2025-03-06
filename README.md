configuring IPV6 ACLS
 
Part 1: Configure, Apply, and Verify an IPv6 ACL  
R1
step1
deny tcp any host 2001:DB8:1:30::30 eq www
deny tcp any host 2001:DB8:1:30::30 eq 443 
permit ipv6 any any  
 step 2
interface GigabitEthernet0/1  
 ipv6 traffic-filter BLOCK_HTTP in 
(Step 3: Verify the ACL implementation.  
Verify that the ACL is operating as intended by conducting the following tests:  
• Open the web browser of PC1 to http://2001:DB8:1:30::30 or https://2001:DB8:1:30::30. The website 
should appear.  
• Open the web browser of PC2 to http://2001:DB8:1:30::30 or https://2001:DB8:1:30::30. The website 
should be blocked.  
• Ping from PC2 to 2001:DB8:1:30::30. The ping should be successful. )


Part 2: Configure, Apply, and Verify a Second IPv6 ACL 
R3
step 1
deny icmp any any 
permit ipv6 any any 

step 2
interface GigabitEthernet0/0  
ipv6 traffic-filter BLOCK_ICMP out  

(Step 3: Verify that the proper access list functions.  
a. Ping from PC2 to 2001:DB8:1:30::30. The ping should fail.  
b. Ping from PC1 to 2001:DB8:1:30::30. The ping should fail.  
Open the web browser of PC1 to http://2001:DB8:1:30::30 or https://2001:DB8:1:30::30. The website 
should display.)
