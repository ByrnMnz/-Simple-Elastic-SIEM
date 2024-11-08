# Simple Elastic SIEM Home Lab
# Project

This lab is dedicated to creating and understanding the basic concepts of an Elastic Stack Security Information and Event Management (SIEM). Using Abdullahi Ali's online guide, I will use virtual machines to generate events on the Kali VM, set up agents to forward data to the SIEM, and query and analyze the SIEM logs. 

Abdullahi Ali's guide: https://medium.com/@aali23/a-simple-elastic-siem-lab-6765159ee2b2

# Setup
Before starting this project, I had to create an Elastic Cloud account to gain access to the tools needed to create an SIEM.
The first step in this lab is setting up our VMs using a virtual box to download Kali Linux from the following link: https://www.kali.org/get-kali/#kali-platforms

Once Kali Linux has been downloaded, installed, configured, and launched from the Virtual box, we will put the agent on the Kali VM to push audit logs and telemetry up to the SIEM. To do this, head back to the Elastic site, select Add Integrations, and follow up with Elastic Defend. Once prompted, copy the terminal command and paste it into the Kali Linux VM. You will know the agent is installed not only by the command terminal on Kali Linux, but you will also have a confirmation prompt on the Elastic Cloud Site. You can also verify the agent by running "sudo systemctl status elastic-agent.service"

![VirtualBoxVM_APrCyBKhMl](https://github.com/user-attachments/assets/c1ec01ea-69a2-440d-9c50-48ad0ccc8a4f) 

![VirtualBoxVM_QJEOiIABnb](https://github.com/user-attachments/assets/80e347f5-dde8-4343-81ec-9164b12a8ae4)

# Creating Events

Next, we will run commands such as "nmap -p- localhost" to run an end map scan on the Kali box itself and "sudo nmap -sS localhost" to generate security events on the Kali VM, which can be tracked on the Elastic Cloud site. 
On the Elastic Cloud site, I navigated to Observability > Logs > Stream to view all the activities on the VM. To find when nmap commands were run, I searched "process.args: nmap" and selected the three ellipses to pull all the details of what was done in the environment when nmap was run. 

![chrome_830cv2i48S](https://github.com/user-attachments/assets/d3e0470f-d268-4e9d-a797-5470eeba366a)

# Creating a dashboard

With all the data generated by the VM I can create a basic dashboard to analyze logs and identify patterns or anomalies. 

![EPrBNuAg8y](https://github.com/user-attachments/assets/bad99f2c-22d0-45f8-ab4c-ce85f73614b4)

# Creating Alerts
To complete this lab, I'll only create an alert for this lab to detect Nmap scans. To do this, I returned to Elastic Cloud in the security tab, selected Alerts, managed rules, and created a new rule. Under this new rule, I also added a description to remind myself what this alert was for and what it alerted me to. I also used a connector type to alert Slack and Jira to create a ticket for action.  

![chrome_jUcM0qYsUd](https://github.com/user-attachments/assets/48384710-a106-45e2-a062-d7377480db5c)
