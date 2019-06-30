# Ansible :
    
* Anible is an Automation Tool

   
            ------SSH-----> Linux
            ------api-----> Cloud
            ------SSH-----> Network
            ------api-----> Docker
            ------win

            Ansible doesn't support windows
            Ansible is made in python

            // To install Ansible 

            pip3 install Ansible
            yum install ansible (only in redhat)

            [ad]
            baseurl=http://13.234.66.64/summer19/ansible27
            gpgcheck=0


            change password 
            vi /etc/ssh/sshd_config
            line no.65 :  Password Authentication =Yes

            systemctl restart sshd

            ssh ec2-user@ip 

            /etc/ansible/hosts (inventory file)
<!---->
            
            Step1: Pick 2 OS on Cloud
            Step2: OS1 ---> install ansible
            Step3: Assign password to ec2-user in OS2
            Step4: Change etc/ssh/sshd-config to accept passwor authentication=Yes in OS2 and restart sshd service.
            Step5: go to /etc/ansible/hosts in OS1 and enter target IP at either top or bottom As shown
                    [any name]
                    IP  (write any numbers of IPs . Ansible will call by name)

            ansible a -u ec2-user(or root or anything , all target username should be same)

            ansible a -u ec2-user -m ping --ask-pass(or -k)
                -->a is any name given hosts

            ssh-keygen (make key at ansible)
            send public key to OS2
                ssh-copy-id  username@IP (of reciever)
            
            ansible a -u ec2-user -m ping 

<!---->
    MITM (Man In The Middle)
        Check why http -->https
<!---->
    
    mod_ssl : install it and restart .
            your website will start in https  

            ansible a -u ec2-user -k -m command -a "date"

            Modules :   ping    >
                        command     >
                        shell           >
                        debug              > File ---> PlayBook(write in language : YAML)
                        yum             >
                        service     >
                        copy    >
                         requests (in python3 work : data website se nikalke save karna )
<!---->                        
#### Idempotency  ???    
<!---->


     ansible-doc  yum (To check everything about yum module)
     ansible-doc  -l (List of all modules)

    Contribute to ansible...                  
