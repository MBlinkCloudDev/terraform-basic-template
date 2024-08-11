# terraform-basic-template

## Advantages of Terraform
- IaC
- can easily build test environments
- automated documentation

## install terraform on windows
- create "Terraform" folder in C
- paste the binary file (downloaded from https://developer.hashicorp.com/terraform/install#windows) into the folder
- add the absolute path to the folder to the Path-environment-variable
- restart PC

## install Azure CLI on windows
- https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli#install-or-update
- in VS Code, connect to azure account and tenant, run: $ az login

## now try out
 Quickstart: https://learn.microsoft.com/en-us/azure/developer/terraform/create-resource-group?tabs=azure-cli
<--- (use this example, to provision some infrastructure)


Create a directory in which to test the sample Terraform code and make it the current directory.<br>
Create a file named providers.tf (and insert the following code...)<br>
Create a file named main.tf (and insert the following code...)<br>
Create a file named variables.tf (and insert the following code...)<br>
Create a file named outputs.tf (and insert the following code...)<br>


### Now initialize Terraform
$ terraform init -upgrade
(also run "terraform init", when you have a new configuration (or using one pulled down from somewhere), run "terraform init" first)

### create TF execution plan (plan without executing it)
$ terraform plan -out main.tfplan <br>
(save execution-plan in file "main.tfplan")

-> "terraform.tfstate" is created; it is the single source of truth of your infrastructure provisioning (from the execution-plan)

### apply execution plan (apply changes to Azure - add, change, destroy)
$ terraform apply main.tfplan


### (optional) destroy the applied resources
$ terraform destroy



# Terraform is modular  --  for scaling

"main.tf" can contain everything.
Bur we need divide code into reusable parts, in modules.
All content in any ".tf" file is used for the execution-plan. It does not matter where we write snippets, but it makes sense for internal structure.

"variables.tf" file can contain variables. The variables' attributes can be used in the "main.tf" file, using: "var.attr>". <br>
"terraform.tfvars" file can contain variables + their values, and this updates the default values of variables in the "variables.tf" file. <br>
"output.tf" file can output some data, while (resources?) running in a pipeline. E.g. you want to obtain some public IP address from a service, or know if it's running.
--> $ terraform output    <--- shows you the output in the CLI.


# Terraform Use Cases

- you can build a huge application
- then provision it on Azure in 30s
- then do your work with the application
- then destroy the Azure resources in 30s




# Links & Resources
- https://github.com/scraly/terraform-cheat-sheet/blob/6891067aa711d07cefed1ea2fb5582fa49c4d31e/terraform-cheat-sheet.pdf
- https://spacelift.io/blog/terraform-commands-cheat-sheet
