	1. Which components you have created using terraform?
I have created resource group, security account, N/W security group, VMs using azure providers and Vmware providers.

	2. How to do changes of already created resources in terraform?
The terraform import command imports existing resources into Terraform.
terraform import [options] ADDRESS ID

	3. When u run terraform , state file gets created, where u store that state file?
State file maintains a state that maps the current status of  infra with config file.
State file is stored either on the local machine or remote storage location like storage account in azure or S3 bucket in AWS cloud, we can also store it in TF cloud but by default it is stored in local machine named as terraform.tf state file.
State file can contain sensitive info also, so it is recommended to store it on media that is encrypted.

	4. If u loose state file, how to resolve?
Losing the Terraform state file can be problematic because it contains critical information about your infrastructure's current state and the relationships between resources. Without the state file, Terraform loses the ability to determine what resources it's managing and how they are configured. 
Backups: If you have regular backups of your state file, you can restore it from a backup. This is why it's recommended to back up your state files in a safe and secure location.

Recreate Infrastructure: If you have access to the configuration files used to create the resources, you can recreate the infrastructure by using those configuration files. However, Terraform will treat this as creating entirely new resources, which might lead to conflicts if the existing resources weren't manually destroyed.

Reimport Resources: If some of the resources are still available in your cloud environment, you might be able to import them back into Terraform's state. The terraform import command allows you to import existing resources into Terraform's management. This can be complex, as it requires manually matching resources in the cloud with the corresponding resource configurations in your Terraform configuration files.

Collaboration and Documentation: If you're working in a team, check if any of your team members have a copy of the state file. If not, gather information about the resources from cloud provider consoles, APIs, or other documentation. While this won't recover the state directly, it can help you recreate your infrastructure configuration more accurately.

Rebuilding and Testing: In the worst-case scenario where the state is entirely lost and there are no backups or documentation available, you might need to start from scratch. This involves recreating your infrastructure configuration, testing thoroughly, and making sure the new resources match the desired state.


	4. List some features of terraform?
It works on multiple cloud providers- like AWS, azure, GCP, Vmware
Its uses HCL lang, which human readable, it help me to IAAC code quickly
Hashi corp config lang

	5. Terraform validate command - it is used to validate the syntax of tf file. Terraform performs a syntax check on all Terraform files in the directory specified and displays warnings and errors if any files contain invalid syntax.
	6. Common errors catched by TF validate command- Syntax error, unknown resources or service providers, missing attributes, invalid arg name, invalid arg id, unused variable

	7. IAC or Infrastructure as Code allows you to build, change, and manage your infrastructure through coding instead of manual processes.
	8. Life cycle block- In Terraform, the lifecycle block is used to control how certain resources are managed over their lifecycle.
	9. Common config settings- Create before destroy, prevent destroy, ignore update
	10. Terraform vs. Ansible-
	Business should choose according to their needs-
	TF- can be used if we want to build infra from scratch, 
	     declarative approach, 
	     helps in maintaining steady state, without much intervention
	Ansible- procedural approach, 
	               config or manage infra evolving or changing over time.
	Updating already configured env
	
	11. terraform Destroy- terraform destroy -target=resource_type.resource_name
	12. How to store keys-> env variables, tf variables, secrect mgmt tools
	13. Modules- 
	  Root Module- Is the main directory that works with .tf files. It can have n number of choild or published modules.
	Child module- Any module that can be called by another module (usually the Root module) is considered a child module.
	Published Modules are modules pushed to a private or public repository.
	
	14. A remote backend in Terraform refers to an external storage and management system for storing the Terraform state file, which contains information about the current state of your infrastructure resources. Using a remote backend is a best practice in Terraform for several reasons, including collaboration, data persistence, and security. Remote backends provide a centralized and controlled way to manage and access the Terraform state.
	15. Examples- Hashicorp tf cloud, AWS S3 , Azure storage, google cloud storage
	16. How do we provide variables at the runtime?
	Usually variables are stored in a file called var.tf, You can pass variables directly to the terraform command using the -var flag. Or by .tfvar file using -var-file flag to provide values
	17. Can we manage tf code into multiple environments- yes by using tf workspace or usable modules
	18. Cloud formation vs. TF- 
	CF- YAML or JSON
TF- HCL
