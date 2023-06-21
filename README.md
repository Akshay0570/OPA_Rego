# OPA_Rego

•	Installed Tf-cli and OPA and Aws-cli
•	Created tf file name aws.tf for creating Aws Vpc and subnets
* Initialize the Terraform configuration
$ terraform init
# Generate the execution plan( faced error while executing terraform plan have to delete “.tfstate” file )
$ terraform plan -out="plan.tf"
# Convert the execution plan to JSON
Faced error while running below command and it is resolved by changing the permission of the directory on which you are working in.
$ terraform show -json "plan.tf" > "plan.json"
# Start the interactive shell
$ opa run plan.json
# View the contents of the data document
$ data
# View the top level keys of the data document
$ data[keys]
# created package
$ package terraform
# imported input
import input.tfplan as tfplan
# For policy code refer to the file with extension ".rego"
# Check the Terraform plan against the OPA policy
opa eval - format pretty - data FILENAME.rego - input FILENAME.json "data.terraform"
# Explanation about above command
* opa eval ---> evaluating the Opa policy code
* - format pretty ---> converts it to the human readable format
* - data FILENAME.regi ---> data file which contains policies written with the ".rego" extension
* - input json ---> input file name which created in ".json" format
* "data.terraform": ---> It is the query which we want to perform 
