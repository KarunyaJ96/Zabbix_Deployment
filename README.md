# Zabbix_Deployment -
-----------------------------------------------------------------------------------------------------------------
Ansible playbook deploys a Zabbix infrastructure using Docker containers and monitors CPU utilization on specified hosts. Overview of the playbook:

Deploy Zabbix Docker Infrastructure:

Create Docker Network for Zabbix:
Creates a Docker network named "zabbix-net."

Start MySQL Container:
Launches a MySQL Docker container with the necessary environment variables for Zabbix configuration.

Start Zabbix Java Gateway Container:
Starts a Zabbix Java Gateway container.

Start Zabbix Server Container:
Launches a Zabbix Server container, connecting it to the "zabbix-net" network.

Start Zabbix Web Interface Container:
Starts a Zabbix Web Interface container, connecting it to the "zabbix-net" network.

Onboard New Instances:
Add new instances to the inventory:
Adds new instances to the inventory with the provided details.

Install Zabbix Agent on new instances:
Installs the Zabbix Agent on the newly added instances.

Configure Zabbix Agent:
Configures the Zabbix Agent on new instances using a Jinja2 template.
Notifies the "restart zabbix-agent" handler.

Handlers:
Restart Zabbix Agent:
Restarts the Zabbix Agent service when triggered.

Monitor CPU Utilization:
Gather CPU facts:
Uses the top command to get CPU utilization stats on hosts.

Debug CPU facts:
Prints the gathered CPU statistics for debugging purposes.

Trigger email if CPU exceeds 50%:
Uses the Zabbix API to create an action that triggers when CPU utilization exceeds 50%.
Sends an email alert to the specified user when triggered.

