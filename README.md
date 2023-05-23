# SplunkReboots
Ansible roles to manipulate Splunk clusters, particularly to automate reboots after OS patches

## Basic Order of Operations
1) Check all servers in inventory with ping to see who's alive
2) Work on the Cluster Manager: 
  
    a. Enable maintenance mode
  
    b. Reboot the server
  
    c. Wait for it to ping again
  
    d. Verify that Splunkd starts up

3) Work on the Indexers, serially, one at a time:
  
    a. Reboot the server
  
    b. Wait for it to ping again
  
    c. Verify that Splunkd starts up

4) Work on the Deployer and Search Heads: 
  
    a. Reboot the server
  
    b. Wait for it to ping again
  
    c. Verify that Splunkd starts up

5) Work on the Cluster Manager again:
  
    a. Disable maintenance mode

## Role Descriptions
### indexer_offline
Executes ```splunk offline``` on a Splunk clustered indexer

### reboot
It...reboots

### rhel_restart_splunk
Not used; leftover from the fork and preserved for possible future use

### splunk_cm_maintenance_mode_enable/disable
Executes ```splunk <enable\disable> maintenance-mode``` on a Splunk cluster manager

### splunk_server_common
Not used; leftover from the fork and preserved for possible future use

### verify_splunk_status
Checks for connectivity on port 8089 and verifies the Splunkd systemd service is running

### verify_status
A simple ping test to check who's alive and who isn't
