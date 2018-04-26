## Terraform Udemy Tutorial
[Link To Course](https://www.udemy.com/learn-devops-infrastructure-automation-with-terraform/learn/v4/overview)

#### What is Terraform?
* It allows you to write infrastructure as code
* You could go into web cosole and spin up instances but that is manual
* Terraform allows you to write it in code 
* It is the automation of your infrastructure 
* Keep your infrastructure in a certain state
* Makes your infrastructure auditable
    * You can keep version control of your infrastructure which allows you to keep track all of past versions
    
* Highly recommended to use the `out.terraform` file

* Run `terraform plan` just shows changes would be made
* Run `terraform apply` to apply the changes or `terraform apply changes.terraform`
* `terraform plan -out changes.terraform` to monitor all changes
* `terraform destroy` will destroy all resources. Do not use in production     


#### Variables
* Used to hide secrets
* Used for elements that might change
    * AMIs are different per region
* Easier to re-use the files
* `${var.NAME}`
* Then in the file `variable "NAME" {}`

* Can put secrets in `terraform.tfvars` and never put this in your version control 


#### Using Vagrant 
* It is a software produshed by HashCorp
* Vagrant is a virtual machine. To start it you can use `vagrant up`, this will start it
* You can then ssh into 

#### Provisioning Software
* 2 ways to provision software
* You can build your own custom AMI and bundle your software with the image
    * Packer is a great tool 
* Another way is to boot standardized AMIs, and then install the software you need
    * Chef, Puppet or ansible
* Chef is integrated within Terraform, you can add chef statements
    
#### File Uploads
* You can use `connection` in terraform to connect to a host
* can upload scripts using `provisioner` and "remote-exec"

### Output
* You can use Output to display IP address of an AWS resource
* you can refer to any attribute by specifying the following elements in your variable: 
    * Resource Type: aws_instance
    * Resource name: example
    * Attribute name: public_ip
* You can populate IP addresses in an asnbile host file
  
#### Terraform State
* Terraform keeps remote state of the infrastructure
* It stores it in a file called terraform.tfstate
* This is how terraform keeps track of the remote state
* If the remote state changes and you hit terraform apply again, terraform will mke changes to meet the correct state again
* You can version control your terraform state files 
*  **BACKEND FUNCTIONALITY**: Can be saved unsing backend functionality 
    * s3 (with locking mechanism using dynamo DB)
    * consul (with locking mechanism)
    * Terraform Enterprise ($$$)
    * Allows for collaboration, remote state will always be available for entire team, can use S3
    * State file is not stored locally, sensitive information is now only stored remotely.      

###### Configure the backend:   
   1. Add the backend code to the .tf file (save a file called backend.tf)
        * You can use `consul` ![Link To Image](http://res.cloudinary.com/thefinleycode/image/upload/v1517894005/Terraform-backend-consoul.png)
        * You can also store state in s3 ![Link To Image](http://res.cloudinary.com/thefinleycode/image/upload/v1517894086/Terraform-backend-s3.png)
   2. Run the initiailization process
        * type Terraform init and will show you a message that the backend has been configured
   
  This way is nice because its easier to manage
  * You can also specify a read-only remote store directly in the .tf file.
  
  
#### DataSources
* Datasources provide you with dynamic information 
  * List of AMIS or List of avilability Zones
* Another example is the datasource that gives you all IP adressses in use by AWS
    * Eg allow all traffic from amazon instances in EU
    * Filtering can be done using security groups in AWS
    * Example of a data source: ![Example of filtering ip address](http://res.cloudinary.com/thefinleycode/image/upload/v1517898010/terraform-datasources.png)

#### Template Provider 
  * Can help create customized config files
  * Build templates based on vairables from terraform resource attributes
  * Cloud init config files can run commands when an instance first starts 
  Example of how the template provider is used: ![Template Provider](http://res.cloudinary.com/thefinleycode/image/upload/v1517899118/terraform-template-provider-could-config.png)
  
#### Other Providers
  * AWS most popular but potentially any company has an api could be a proivider
  * Google, Azure, Heroku and ditigal ocean
  * Github for version control
  * See list: https://www.terraform.io/docs/providers/
  
#### Modules
* These make your code more re-usable
  * Use third party modules
  * Reuse parts of your code, eg: set up a VPC in AWS
  
  
#### Terraform Command Overview
  * `terraform apply` = applies state
  * `... destroy` = destroys all terraform managed state
  * `fmt`  = rewrite terraform confirugation to a canonical format and style 
  * `get`  = downloads and updates modules 
  * `graph` = create a visual representation of a configuration or execution plan
  * `output [options][NAME]` = output any of your resources
  * `plan` = show the changes to be made to the infrastructure
  * `refresh` = can refresh remote state, and can identiy differences state file and remote state
  * `remote` = configure remote state storage
  * `show` = show human readable output from a state of a plan
  * `state` = advanced state management
  * `taint` = manually mark a resource as tainted, will be destructred and recreated at next apply
  * `validate` = validate your terraform syntax 
  * `untaint` = undo a taint
  * `import [options] ADDP ID ` = you can import an existing resource  with the address and the ID
  
  
  ## Terraform with AWS
  1. Start by creating a VPC, Internet Gateway, Route Tables, subnets and NAT in order to launch all resources (or you can use the default VPC)
  2. Launch EC2 instances
  
  #### VPCs
  * Virtual Private Network - created by default
  * VPC isolates the instances on a network level
  * Always launch instances in a VPC - **BEST PRACTICE**
  * You could link VPCs which is called peering
  * Instances launched in subnet zones will have a public ip corresponding to the zone #, ie. zone 3 will have pulic ip of 10..0.3.x
  * Private subnets started on 10.0.4.x which would be an IP for instance in zone 1.
  
  #### Private Subnets
  * Private subnets can only be from the following: 
  ![PrivateSubnests](http://res.cloudinary.com/thefinleycode/image/upload/v1518055928/PrivateSubnet.png)
  * Subnet-masks
  ![SubnetMasks](http://res.cloudinary.com/thefinleycode/image/upload/v1518056164/subnet-masks.png)
  * Things to store in private subnets are: 
    * Databases, caching services, and backendss
    
 #### Launch Ec2  
 * To spin up an Ec2 you need: 
    1. Specify the Provider `provider.tf`
    2. The instance in the `instance.tf `
    3. And specify you variables in the `vars.tf`
  * IMAGE EXAMPLE: 
    ![EC2](http://res.cloudinary.com/thefinleycode/image/upload/v1518149233/EC2-Setup.png)
   * In order to ssh into the instance you need to install the public key pair
    
    
  #### Security Groups
   * Ingress is inbound uses
   * Outgress is outbound rules
   * EXAMPLE security tf file:
    ![security group](http://res.cloudinary.com/thefinleycode/image/upload/v1518149491/security-group.png)
    
 
 #### SSH Commands
 * `df -h` while ssh into AWS instance shows you what is on your instance
 * `mkfs.ext4 [FILEPATH]` creates a file system on the drive
 * To ssh into Ec2 instance `ssh -i [keyname] -l ubuntu [publicIP] `