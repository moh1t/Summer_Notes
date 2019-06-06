Cloud computing --> Virtual computing
    Distributed processing 
    Software as a service -- Saas - Like AutoCAD for a duration. Google Docs is also a kind of saas. 
    Companies providing Saas - Google , Mirosoft , No AWS-- AWS doesnot provide Saas.

    STaaS- Storage as Service -> AWS, OpenStack, Azure, BluMix-- in development phase. RackSpace.

    IaaS- Infrastructure as a Service--> AWS, Azure, GCP, 

    PaaS- Platform as a service.--> AWS Lambda--Backend Containers. AZure App Service, Azure Fabric Service--Backend Containers. 

    NAAS- Network as a Service. --> Same Private ip as your local system on the cloud Infrastructure. Including all like firewall dhcp. AWS- VPC- Virtual private  Cloud, Azure-Network.

    DBaaS- Database as a Service --> 
        AWS- SQL - RDS(product name like ec2 , includes MySQl, SQlite)
            NoSQL - DynamoDB

    MLaaS- Machine as a Service - Paid - Not in Mumbai. Only in afew region.


STaaS- AWS Types --
    1. Object -- Google Drive. Non technical , upload, Download and share data - AWS - S3 , Simple Storage Service.
    2. Block -- EBS
    3. File -- Compressed data from Block or Object, Costs approx 1/40 of others. AWS Glacier.

Task -- Upgrade default storage in ec2 case 
    1. when OS is shut down 
    2. When OS is running

lsblk to check attached harddisks.
types of cloud --
    1. standard
    2. private 
    3. hybrid
    

---> UDP socket programming --

Receiever ->
Steps--
netstat -nulp -> IP & port  -> bind -> Recv -> allow port

netstat -nulp --> To check currently used port numbers in udp protocol. u stands for udp in nulp . Replace u with t in nulp to check tcp running port number ntlp . & p stands for programs we want to check the name of program which is using the port.


--> Cases --AWK /profiles.d 

31/May/2019--- >>

Storage as service --
    Object -- Google drive , cant format , Cant install os , S3 on aws --Simple storage service 
    Block -- EBS - RAw space, Can be formatted, can crate or delete partition


            AWS-S3                  |||     Google Drive
  1.can store any type of data       |     This too
 2. doesnt provide software as a     |     Provides Software as service along  
    service along with it            |    with like You view photos , open excel as service

3. free upto 5 GB                    |   free upto 15 GB

4. Unlimited but have to pay bill    |   have to define storage previously,
monthly .                            |    like pay in advance for how much space or each month whether you use it or not.

5. Can host static websites          |  cant host websites
    seems like apache + Storage 

6. Use uploades photos to directly   |  cant user photos directly to web pages
    webpages 

7. highly available than Gdrive



AWS S3 --- SDS --> Software define storage. -- Bucket like Gdrive in google storage service
Bucket and Grive is like folders 
.. No region for S3, You can set region for Bucket
.-> Bucket name must be unique. 
~ Bucket cant also have Folders for data management
~ Store info about data in key value pair. 
~ Que - launch ec2 nginx, create html page use image from S3
2... If possible mount your s3 bucket in ec2 instance.
    If mounted store some images and pdfs 
3.. Do S3 configure bucket from awscli 

to list data from bucketname
    aws s3 ls s3://bucketname
To upload data to bucket
    aws s3 cp p1.html s3://rogers-bucky
to create bucket mb
    aws s3 mb s3://bucketname
to remove bucket from aws s3 use rb-- r for remove b for bucket
task ---> downlod , set permissions, update data.

s3 advance.. -->
    1. website hosting (static -- Only frontend language without any backend lanuage)
        Only static can be hsoted by s3 storageservice.

01/06/2019-->

Version --> Versioning in s3 --> Not Free or free tier eligible.
    Versioning in S3 cannot be disabled once enabled. It can only be suspended.

USER management -->

    Create Group --> Provide access to the group --> add users to the group
        access in aws known as policy
        

S3 --
Life cycle -->
    Transition-->
         What will be the life cycle of objects. Like all objects after how much days need to be commpressed wheteher should be originally commpressed/ current version should commpressed or the previous version should be commpressed. 
        Storage Class--
            Standard IA --> Infrequent access 
            Intellignet -Tierirng --> Commpressed.
##          Transistion to glaciers after ---> highly commpressed. 

    Expiration -->
        clean up expired objects. -->
            What do with duplicate objects by name or by content like should be deleted after 7 days
            -- For incomplete objects
            -- 


Replication of bucket-->
    Replication of object should be in different regions. 
        In which storage class like standard IA, Intelligent Tiering, Glacier, Glacier-Archive.

Inventory --> Like Store Room
    Everything Not needed for now must be kept into inverntory..

Analytics --> 
    Analyzing your data like strorage uses and Whom So ever is accessing data if some is writing a file again and again. 

Glacier is not auto scalable. --> You need to enable Auto scaling differnetly.


        