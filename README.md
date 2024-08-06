# terraform-basic-template

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


# Terraform is modular

"main.tf" can contain everything.
Bur we need divide code into reusable parts, in modules.
All content in any ".tf" file is used for the execution-plan. It does not matter where we write snippets, but it makes sense for internal structure.

"variables.tf" can contain variables. The variables' attributes can be used in the "main.tf" file, using: "var.<attr>".
