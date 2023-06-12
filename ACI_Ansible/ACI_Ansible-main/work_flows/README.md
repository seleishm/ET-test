 # Work Flow playbooks:
 
 ####  CONFIGURE INVENTORY - apic(s) hostname and credentials in `ADP_Health_Checks_w_BPs/demo_aci_bp_inventory.yml`:

```
fabric01:
  hosts:
    apic1:
      aci_hostname: 172.31.2.30
      aci_username: admin
      aci_password: C1sc0TTG!
```

#### Playbooks:
- [Deploy vlan on port](https://wwwin-github.cisco.com/ADP-Automation-Team/ACI_Ansible/tree/main/work_flows#deploy-vlan-on-port)
- [Create (2) Tier Application/setup_app_profile](https://wwwin-github.cisco.com/ADP-Automation-Team/ACI_Ansible/tree/main/work_flows#create-2-tier-applicationsetup_app_profile)
- [Deploys Static Path binding for given EPG](https://wwwin-github.cisco.com/ADP-Automation-Team/ACI_Ansible/tree/main/work_flows#deploys-static-path-binding-for-given-epg)
- [Set Up VPC](https://wwwin-github.cisco.com/ADP-Automation-Team/ACI_Ansible/tree/main/work_flows#set-up-vpc)
- [Setup/Create Tenant with Vrf & L3Out](https://wwwin-github.cisco.com/ADP-Automation-Team/ACI_Ansible/tree/main/work_flows#setupcreate-tenant-with-vrf--l3out)
 
## Deploy vlan on port
   - #### To run: `\work_flows> ansible-playbook -i inventory deploy_vlan_on_port/deploy_vlan_on_port.yaml`
     - Upon successful execution of this Ansible playbook work flow, it POSTS/Creates APIC objects for deploying a vlan on leaf port including:
       - Create vlan pools 
       - Assign VLANs to pool
       - Creates physical domain
       - Assign the VLAN Pool to Physical Domain
       - Create Access Entity Profile 
       - Associate the AAEP to the Physical Domain
       - Create Interface Policy Group with the AAEP
       - Create Leaf Switch Profile 
       - Create Leaf Switch Selector 
       - Create Leaf Interface Profile
       - Bind Leaf Interface Profile to Leaf Switch Profile
       - Create Access Port Selector  in Leaf Interface Profile
       - Create Port Block in the Access Port Selector

     
      
     
     #### Variables file is referenced within playbook via: 
      - `work_flows/deploy_vlan_on_port/variables_vlan_pool.yaml`
 
 
     
 
## Create (2) Tier Application/setup_app_profile
   - #### To run: `\work_flows> ansible-playbook -i inventory setup_app_profile/setup_app_profile.yaml`
     - Upon successful execution of this Ansible playbook work flow, it POSTS/Creates APIC objects: Tenant, Vrf, Bridge Domain, Application Profile, (2) EPGs (WEB and DB),              filters with entries, Contracts with subjects for EPGs and Domains are bund to the EPGs.
     - Playbook Creates  (2) Tier Application for WEB and backend Database

     
     
     #### Variables file is referenced within playbook via: 
     - `work_flows/deploy_vlan_on_port/variables_app_profile.yaml`
     
     
     
## Deploys Static Path binding for given EPG
  - #### To run: `\work_flows> ansible-playbook -i inventory bind_vpc_epg/bind_vpc_epg.yaml`
     - Upon successful execution of this Ansible playbook work flow, it POSTS/Creates APIC objects for deploying a Static Paths binding for a given EPG.
     - Deploy Static Path binding for given EPG

     
     
     #### Variables file is referenced within playbook via: 
    - `work_flows/deploy_vlan_on_port/variables_epg_bind.yaml`
    
    NOTE: The assumption is that the Tenant, vrf, Bridge Domain, EPG, vlan pool and  domain associated with the Static Binding’s variables have been created prior that are used            for this playbook.
    
## Set Up VPC
  - #### To run: `\work_flows> ansible-playbook -i inventory setup_vpc/setup_vpc.yaml`
     - Upon successful execution of this Ansible playbook work flow, it POSTS/Creates APIC objects for deploying a virtual port channel for two given nodes. 
     - Workflow:
       - Create Port Channel Policy
       - Create a Virtual Port Channel (VPC) Interface Policy Group
       - Create Leaf Switch Profiles for each node
       - Create Leaf Switch Selectors for each node
       - Create Leaf Interface Profiles for each node
       - Associate Interface Access Port Selector to Leaf Interface Policies for each node
       - Associate an access port block to an interface selectors for each node
       - Bind interface profiles to leaf profiless for each node

     
     
     #### Variables file is referenced within playbook via: 
    - `work_flows/setup_vpc/variables_vpc.yaml`
    

## Setup/Create Tenant with Vrf & L3Out 
  - #### To run: `\work_flows> ansible-playbook -i inventory create_l3out/create_l3out.yaml`
     - Deploys a tenant with vrf and associate an L3OUT.  
     - Workflow:
       - Create Tenant 
       - Create/assign a Vrf within Tenant 
       - Create Bridge Domain 
       - Create Contract: Create Contract from External EPG to EPG via selecting AP;   assigning  L3OUT; assign External EPG and create contract specifying all traffic.    
            - w/ Subject 
            - w/ filter 
            - w/ Filter entries 
       - Create AP 
       - Create EPG: For EPGs to Advertise externally; Choose the Bridge Domain subnet and configure as “Advertise Externally”.  
       - Create L3OUT within VRF 
            - w/  L3Domain  
            - w/ Bridge Domain:  Associate the Subnet’s Bridge Domain to the L3OUT 
            - w/ vrf 
            - w/ L3 route protocol (EIGRP) 
            - w/ ASN # 
            - add external prefix (external EPG): to associate/classify learned prefixes into  External EPG 
            - assign node : assign L3OUT to Border Leaf/s interface/s and assign IP address 
                - assign interface from node 

     
     
     #### Variables file is referenced within playbook via: 
    - `work_flows/create_l3out/variables_l3out.yaml`
