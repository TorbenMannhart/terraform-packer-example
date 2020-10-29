# Learn Terraform Provisioning
followed tutorial: https://learn.hashicorp.com/tutorials/terraform/packer?in=terraform/provision
#to run app:
1. run `cd instances`
1. run `terraform init && terraform apply`
1. connect to instance: `ssh terraform@$(echo "aws_instance.web.public_ip" | terraform console) -i ../tf-packer`
1. navigate to web-app dir: `cd go/src/github.com/hashicorp/learn-go-webapp-demo`
1. run: `go run webapp.go`
1. open browser and enter `<instance-ip>:8080`
## when testing is finished run `terraform destroy`



#tutorial instructions:
1. create ssh-key:
`ssh-keygen -t rsa -C "your_email@example.com" -f ./tf-packer`
1. build packer image in images:
`packer build image.json`
1. change ami in instances/main.tf with the resulting ami from step 2
1. create file: `terraform.tfvars` and input same region as in packer image (images/image.json) here:
`region = "us-east-1"`
1. run `terraform init && terraform apply`
1. connect to instance: `ssh terraform@$(echo "aws_instance.web.public_ip" | terraform console) -i ../tf-packer`
1. navigate to web-app dir: `cd go/src/github.com/hashicorp/learn-go-webapp-demo`
1. run: `go run webapp.go`
1. open browser and enter `<instance-ip>:8080`
## when testing is finished run `terraform destroy`
