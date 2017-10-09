READ ME
--------

The Service Scaling foler consists of:
1. Heat Template (Service_Scaling_template.yaml)
2. Environment file(Service_Scaling_env.yaml)
3. Instance deployment template (service_instance.yaml)
4. Initial-configuration file (nit-cfg.txt)
5. bootstrap (Service_Scaling_bootstrap.xml)

## There is an authcode file included in the template; which is optional



DIRECTIONS FOR USE:
-------------------

1.Copy and  upload the PAN image using the horizon UI or through glance :
>$ glance image-create --name <NAME> --disk-format qcow2      --container-format bare      --file <IMAGE_FILE> 
root@node-8:~# glance image-create --name PAN-8.0 --disk-format qcow2 --container-format bare --file PAN-8.0.qcow2

Step2: Confirm the image presence by doing : “glance image-list” on the contrail controller. The image uploaded should be listed in this output. 
Also there should be a default image “TestVM” provided by openstack. [Ubuntu cloud image has been used to validate the traffic flow; details provided under "Validation"]

Step3: Copy files 4 and 5 [ 4.Initial-configuration file (init-cfg.txt) 5.bootstrap (Service_Scaling_bootstarp.xml)] onto controller node.
Make folders in the hierarchy mentioned below and move the files here:

root@node-8:~/bootstrap/config# pwd
/root/bootstrap/config
root@node-8:~/bootstrap/config# ls -ltr
total 36
-rw-r--r-- 1 root root    55 Mar 13 17:57 init-cfg.txt
-rwxr-xr-x 1 root root 13801 Apr  3 21:36 Service_Scaling_bootstarp.xml
root@node-8:~/bootstrap/config#

#if authcode file is required; it can be put in the same folder as mentioned above.

Step4:Copy the first three files [1. Heat template (Service_Scaling_template.yaml) 2. Environment file (Service_Scaling_env.yaml) 3. Instance deployment template (service_instance.yaml)] 
onto the contrail controller node.

Upon completion of all the above steps try the below command on controller:


Syntax: heat stack-create -e <env_file_name> -f <template_file_name> <stack_name> 

root@node-10:~# heat stack-create -e Service_Scaling_template.yaml -f Service_Scaling_env.yaml  Scaling