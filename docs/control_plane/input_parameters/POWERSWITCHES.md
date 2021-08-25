# Dell EMC PowerSwitches  

## Update the input parameters 
Under the `control_plane/input_params` directory, edit the following files:
1. `base_vars.yml` file: Update the following variable to enable or disable Ethernet switch configurations in the cluster.  

	Variable	|	Default, choices	|	Description
	-------	|	----------------	|	-----------------
	ethernet_switch_support	|	<ul><li>**false**</li><li>true</li></ul>	|	Set the variable to "true" to enable Ethernet switch configurations.  

2. `login_vars.yml` file:  Enter the following details to configure Ethernet switches.  
	a. `ethernet_switch_username`- username for Ethernet switches.  
	**NOTE**: The username must not contain the following characters: -, \\, "", and \'  
	b. `ethernet_switch_password`- password for Ethernet switches.   
	**NOTE**: Minimum length of the password must be eight characters and the maximum limit is 30 characters. Do not use these characters while entering a password: -, \\, "", and \'  

3. `ethernet_vars.yml` file: If **ethernet_switch_support** is set to "true" in the *base_vars.yml* file, then update the following variables.

	Variables	|	Default, choices	|	Description
	----------------	|	-----------------	|	-----------------
	os10_config	|	<ul><li>"interface vlan1"</li><li>"exit"</li></ul>	|	Global configurations for the switch.
	os10_interface	|	By default: <ul><li>Port description is provided.</li> <li>Each interface is set to "up" state.</li>	|	Update the individual interfaces of the PowerSwitch S3048-ON (ToR Switch). </br>The interfaces are from **ethernet 1/1/1** to **ethernet 1/1/30**. For more information about the interfaces, see the *Supported interface keys of PowerSwitch S3048-ON (ToR Switch)* section in the README file. </br>**NOTE**: The playbooks will fail if any invalid configurations are entered.
	save_changes_to_startup	|	<ul><li>**false**</li><li>true</li></ul>	|	Change it to "true" only when you are certain that the updated configurations and commands are valid. </br>**WARNING**: When set to "true", the startup configuration file is updated. If incorrect configurations or commands are entered, the Ethernet switches may not operate as expected.   
	
## Deploy Omnia Control Plane
Before you configure the Dell EMC PowerSwitches, you must complete the deployment of Omnia control plane. Go to Step 8 in the [Steps to install the Omnia Control Plane](../../INSTALL_OMNIA_CONTROL_PLANE.md#steps-to-deploy-the-omnia-control-plane) file to run the `ansible-playbook control_plane.yml` file.  