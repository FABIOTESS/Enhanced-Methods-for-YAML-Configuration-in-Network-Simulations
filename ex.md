```diff
!**subnets**: [1, 1, 1, 1, 1]  
!**topology**: [  
!    [0, 0, 1, 0, 1, 0],  
!    [0, 0, 0, 1, 0, 0],  
!    [1, 0, 0, 1, 0, 0],  
!    [0, 0, 1, 1, 1, 0],  
!    [0, 1, 0, 0, 0, 0],  
!    [1, 0, 0, 0, 0, 0]  
]  -> these are the instructions (ps.! is not needed is to format color in md)
```
<mark>
sensitive_hosts:   
    (3, 0): 100  
    (4, 0): 100  
os:  
    - linux  
    - windows  
services:   
    - ssh   
    - http  
processes:   
    - tomcat  
    - apache  
    - nginx  
exploits:  
    e_ssh:  
        service: ssh  
        os: linux  
        prob: 0.8  
        cost: 1  
        access: user  
    e_http:  
        service: http  
        os: windows  
        prob: 0.7
        cost: 1  
        access: user  
privilege_escalation:  
    pe_tomcat:  
      process: tomcat  
      os: linux  
      prob: 1.0  
      cost: 1  
      access: root  
    pe_apache:  
      process: apache  
      os: windows  
      prob: 0.9  
      cost: 1  
      access: root  
service_scan_cost: 1  
os_scan_cost: 1  
subnet_scan_cost: 1  
process_scan_cost: 1  
host_configurations:  
    (1, 0):  
      os: linux  
      services: [ssh, http]  
      processes: [tomcat, apache]  
      firewall:  
        (3, 0): [ssh]  
        (4, 0): [http]  
    (2, 0):  
      os: windows  
      services: [http, ssh]  
      processes: [apache, nginx]  
      firewall:  
        (1, 0): [http]  
        (3, 0): [http]  
    (3, 0):  
      os: linux  
      services: [ssh]  
      processes: [tomcat]  
      firewall:  
        (1, 0): [ssh]  
        (4, 0): [ssh]  
    (4, 0):  
      os: windows  
      services: [http]  
      processes: [apache, nginx]   
      firewall:  
        (1, 0): [http]  
    (5, 0):  
      os: linux  
      services: [ssh]  
      processes: [tomcat, nginx]  
      firewall:  
        (4, 0): [ssh]  
firewall:  
    (0, 1): [ssh, http]  
    (1, 0): []  
    (0, 2): []  
    (2, 0): [ssh]  
    (0, 3): []  
    (3, 0): []  
    (0, 4): [http]  
    (4, 0): []  
    (0, 5): [ssh]  
    (5, 0): []  
    (1, 2): []  
    (2, 1): [ssh]  
    (1, 3): []  
    (3, 1): [ssh]  
    (1, 4): [ssh, http]  
    (4, 1): []  
    (1, 5): [http]  
    (5, 1): [ssh]  
    (2, 3): []  
    (3, 2): []  
    (2, 4): [http]  
    (4, 2): []  
    (2, 5): [ssh]  
    (5, 2): []  
    (3, 4): [ssh, http]  
    (4, 3): [http]  
    (3, 5): []  
    (5, 3): []  
    (4, 5): [ssh, http]  
    (5, 4): []  
**step_limit**: 1000  </mark> -> this is the example
