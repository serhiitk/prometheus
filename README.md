# Monitoring with Prometheus

Install Prometheus and Grafana as *systemd* service. Configure Prometheus for monitoring hosts from github repository **serhiitk/ansible** ( *vm1, vm2, vm3, vm4* ) . 

## Variables
Define variables of Prometheus and Grafana installation in playbook `deploy_prometheus.yml` : 

     prometheus_version: '2.18.1'
     prometheus_data_dir: '/opt/prometheus'
     prometheus_config_dir: '/etc/prometheus'

Define variables of Node Exporters installation in playbook `install_node_exporter.yml` : 

     node_exporter_version: '0.18.1'
     node_exporter_binary_install_dir: '/usr/local/bin'

## Prerequisites
Before starting playbook you must up hosts ( *vm1, vm2, vm3, vm4* ) from github repository **serhiitk/ansible** :

     $ bash vagrant_all_up.sh

## Deploy Prometheus and Grafana
Start deployment Prometheus and Grafana:

     $ ansible-playbook deploy_prometheus.yml

This playbook:

- install Prometheus and Grafana as *systemd* service  
- setting Prometheus monitoring parameters

Prometheus use port `:9090` 
Grafana use port `:3000`  

## Install Node Exporter to hosts ( *vm1, vm2, vm3, vm4* )
Installing and running the Node Exporter on monitoring hosts ( playbook use host group `monitoring_nodes` from `inventory` file ):

     $ ansible-playbook install_node_exporter.yml
