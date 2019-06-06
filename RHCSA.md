RHCSA --
 Password break
 Main machine terminal 
    ssh root@ip_of_vm -X
        -X for gui over SSH --> Like gedit or browser.

    1. Kernel install - using RPM -- DO it at first or not at all do it..
        rpm -ivh url 
        wait for 2 mins untill kernel comes back
        reboot
        Max 5 mins to perform.
    
    Not in order --
        NTP --
            Ping NTP server 
                If you cant ping via name check 
                    vi /etc/resolv.conf 
                        search anything 
                        nameserver IP_OF_NTP_SERVER # --->>>  MUST be an ip not a name Check base machine file in case of conflicts.
            yum install ntp 

            vi /etc/ntp.conf 
                server GIVEN_NTP_SERVER_IP_AND_NAME
            systemctl restart ntpd
            systemctl enable ntpd
            Check after reboot -- Not started automatically 
            vi /etc/rc.local
                systemctl restart ntpd
            chmod +x /etc/rc.local
    
    Selinux
        vi /etc/selinux/config

    To set permission for a sepecific user use setfacl -m u:username:permissions filename.
    

    Set group of directory 
    chgrp PATH_TO_FILE/DIR

    Set Group to new upcoming file/directory Or file/directories to be made in the directory --> 
        SGID -- SET GROUP ID
        sticky bit  SGID(Exam) SUID
        1              2         4
        chmod 2070 path to directory in which files are going to be created works at creating file/directory doesnt work on existing data
            *** Four characters with chmod leads to first number corresponds to special permission like stickybit SGID SUID

IP FORWARDING --
/etc/sysctl.conf
    append --
        net.ipv4.ip_forward = 1
    to check  format 
        sysctl -a | grep ip_forward

    
Search files created by a user 
        create location where you need to save data
    find / -user #username# -exec cp -rvf {} Path_where _to_copy data of user

Create archive --
    create directory of which we need to make tar of.
    go into the directory where you need to save the file 
    pwd = where you need to save the tar file.

    tar -czvf new.tar.gz path_to_directory_of_which_you need to make tar of 

Partition -- 
    i) basic 
    ii) LVM
    iii) swap

    Create new partition
        create 1 extended with full available size 
        create logical partition of given size 
            if You format with xfs ntfs it will be hardisk 
            Go for mkswap if You want to create a partition for swap or ram 
                mkswap /dev/sda5
            
            Instead Of mount go for 
            --> swapon /dev/sda5
    For permanant swap Go to fstab --
    /dev/sda5 swap swap defaults 0 0
    swapon -s ---> To check existing partitions. 

LVM--

Check size of existing partition and format of like xfs 
modify 
    lvextend --size +33M
    For xfs format 
    xfs_growfs /dev/mapper/rhel-home
    For non xfs fromat 
        resize2fs /dev/mapper/rhel-home
    
Extents --> Size will in the multiple of 4MB these chunks are extents
Do swap before lvm 

To change default extent size it can be checked by vgdisplay #vgname#

vgcreate -s 16M #vg name# #/dev/sda6#

vgremove , pvremove , lvremove to remove repectively

mkfs.ext3

mount 
fstab



MOST IMPORTANT QUESTION IN EXAM 

    static ip setting
        ifconfig 
            check lan card name from which we are connected to network 
     cd /etc/sysconfig/network-scrips
     ls
        check for file name same as network card
    vi openfile of same name as network card 
        look for 
            BOOTPROTO="dhcp" --> change dhcp to static
            BOOTPROTO="static"
            Add two more rows 
            IPADDR=192.168.10.149
            NETMASK=255.255.255.0
            GATEWAY=192.168.10.1
            DNS=192.168.10.254

    hostnamectl set-hostname #set hostname to url#
    check resolv.conf for nameserver
Order--

    1. Root password break --> Reboot }     --\
                                                -->  From server without ssh.    
    2. IP static --> Reboot           }     --/   

check gateway on aws --> route -n 


LDAP -- lightweight directory access protocol -> For rhel
AD - active directory --> windows 

LDAP -- HTTP like
LDAPS -- HTTPS like
LDAPS -- Secure lightweight directory access protocol

To connect with LDAPS server
    client needs
        key
        server hostname --(cant be connected by IP)

www.google.com  
        \
         \------>  .com ---> TLD --> Top level domain
                    google.com ---> Domain name 
                    www ---> Host --- like a computer in google.com whose name is www like if you set hostname to a computer xyz.example.com thel its terminal looks like --> root@xyz where xyz is hostname

        st29.adhoc.example.com
        st29 will be host


    For LDAP --> everything except Host --is PREFIX
    to write prefix in LDAP
        st29.example.com
        st29 -host
        prefix dc=example, dc=com


To do LDAP --> 
    ping with domain name should be working
    ping st29.adhoc.com
    NTP should be working
    For LDAP client --> Software needed --> authconfig-gtk

    yum install authonfig-gtk

    authconfig-gtk #--> run 
        A GUI app opens
            select LDAP on the place of local database
            LDAP search base DN -->dc=example,dc=com
            LDAP Server --->ldap://st29.example.com
            Tick tls box
            download ldap 
            set ldap password at place password
            apply then su - given username
            



    TT --> NFS mounts files permanently 
            Autofs mounts file when user logs in and unmouts directory when user logs out.






Order -- #####################################
    root password 
    station number 5 
    ip info
    yum path

    Set IP
    reboot
    kernel
    partition
    Follow the order of question paper



yum install autofs
rpm -qc autofs
auto.master
auto.misc

IN  auto.misc ---> ##-->

ldapuser1   -fstype=nfs,rw,vers=3   station205.example.com:path_to_home directory 


##If it mentioned that we are using version 3 ##

IN auto.master

/home/guests    /etc/auto.misc
##Make sure username is need not be mentioned in this scenerio


systemctl restart restart autofs
systemctl enable autofs
