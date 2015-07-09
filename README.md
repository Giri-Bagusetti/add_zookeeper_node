
Usage
------------------------------------------------------------------------

This playbook is for adding / removing zookeeper nodes to / from the existing zookeeper cluster.


How to use this PlayBook
------------------------------------------------------------------------------------------------------------------

first edit hosts file as shown in the below way

//enter the existing zk clutster details with correct info. you can find tihs info in $ZOOKEEPER_HOME/conf/zoo.cfg file 

[zookeeper_cluster]  
192.168.0.157 zookeeper_id=10 ports=2888:3888

192.168.0.159 zookeeper_id=20 ports=2888:3888

192.168.0.167 zookeeper_id=30 ports=2888:3888

//mention the below information to add a node to the above mentioned cluster.

[add_node]

192.168.0.173 zookeeper_id=40 ports=2888:


if you want to remove any node add ip address / leave this section blank.

[remove_node]

192.168.0.173



finally set the varibles file  in all the roles (./roles/*/defaults/main.yml) which shoulld match with your existing cluster


running the playbooks 
--------------------------------

to add a  node 

ansible-playbook -i hosts add_zk_node.yml -K 

to remove a node 

ansible-playbook -i hosts remove_zk_node.yml -K 



