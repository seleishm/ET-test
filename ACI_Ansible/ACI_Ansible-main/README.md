# ACI_Ansible



### [Health Checks w/ Best Practices](https://wwwin-github.cisco.com/ADP-Automation-Team/ACI_Ansible/tree/main/health_Checks_w_BPs#health-checks-w-best-practices)

### [Workflows](https://wwwin-github.cisco.com/ADP-Automation-Team/ACI_Ansible/tree/main/work_flows)

## Dockerfile available includes image with ansible and cisco.aci pre-installed:

```
docker build . -t ansible
docker run -v ${PWD}:/etc/ansible -it ansible
```
## Testing

Playbooks are tested on [Jenkins Server](https://engci-jenkins-rtp.cisco.com/jenkins/job/team_ADP_Automation_Team/job/ACI_Ansible/) as instructed from [Jenkinsfile](https://wwwin-github.cisco.com/ADP-Automation-Team/ACI_Ansible/blob/main/Jenkinsfile)
