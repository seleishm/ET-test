## Health Checks w/ Best Practices

#### CONFIGURE INVENTORY - apic(s) hostname and credentials in `health_Checks_w_BPs/demo_aci_bp_inventory.yml`:


```
fabric01:
  hosts:
    apic1:
      aci_hostname: 172.31.2.30
      aci_username: admin
      aci_password: C1sc0TTG!
```
### Run all playbooks:
`\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml main.yaml`

### Run Health Check playbooks individually:

- ### Get Fabric Version  
  - Verifies the ACI Major version is `5`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_apic_version.yaml`

- ### Get Control Plane MTU
  - Verifies the Control Plane MTU has a Fabric value of `9000`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_ctrl_MTU.yaml`

- ### Get Data Plane MTU
  - Verifies the Data Plane MTU has a Fabric value of `9000`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_data_plane_MTU.yaml`

- ### Get Disable Remote EP Learn 
  - Verifies the Disable Remote EP Learn is set to `yes`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_disable_remote_ep_learn.yaml`

- ### Get Enforce Subnet Check 
  - Verifies the Enforce Subnet Check is set to `True`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_enforce_subnet_check.yaml`

- ### Get Port tracking 
  - Verifies Port tracking is set to `On`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_port_tracking.yaml`

- ### Get IP Aging
  - Verifies IP Aging is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_ip_aging.yaml`

- ### Get EP Loop protection 
  - Verifies EP Loop protection is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_ep_loop_protection.yaml`

- ### Get Rogue EP Control 
  - Verifies Rogue EP Control is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_rogue_ep_control.yaml`

- ### Get Coop Group Type 
  - Verifies Coop Group Type is set to `strict`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_coop_grp_type.yaml`

- ### Get PTP
  - Verifies PTP is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_ptp.yaml`

- ### Get All VRF info from Fabric validate against BP
  - Verifies VRF Policy Control Enforcement Preference is set to `enforced`
  - Verifies VRF Policy Control Enforcement Direction is set to `ingress`
  - Verifies VRF Dataplane Learning is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_vrf_all.yaml`

- ### Get All BD info from Fabric validate against BP
  - Verifies Data Plane IP Learning is set to `yes`
  - Verifies Limit IP Learning to Subnet is set to `yes`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_bd_all.yaml`

- ### Get MCP interface
  - Verifies Interface MCP is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_interface_MCP_loop.yaml`

- ### Get MCP Global
  - Verifies Global MCP is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_Global_MCP.yaml`

- ### Get DOM
  - Verifies DOM is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_DOM.yaml`

- ### Get DOM feature setting
  - Verifies DOM Feature is set to `telemetry`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_DOM_feature.yaml`

- ### Get BFD on Internal Fabric Interfaces 
   - Verifies BFD on Internal Fabric Interfaces is set to `enabled`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_DOM_feature.yaml`

- ### Get ISIS Metric
   - Verifies ISIS Metric is set to `40`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_isis_metric.yaml`

- ### Get Perserve QoS Dot1q
   - Verifies Perserve QoS Dot1q is set to `dot1p_preserve`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_qos_preserved.yaml`

- ### Get Policy Usage
   - Verifies Policy usage is less than `70%`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_Policy_Usage.yml`

- ### Get Overflow TCAM Usage
   - Verifies Overflow TCAM usage is less than `70%`

    `\health_Checks_w_BPs> ansible-playbook -i demo_aci_bp_inventory.yml get_policy_overflow_tcam_usage.yml`
    
