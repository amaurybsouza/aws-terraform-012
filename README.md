# aws-terraform-012
AWS examples for terraform 0.12

Playing with `terraform-0.12-alpha*` and AWS provider to test some `HCL2` features presented at [this Hashiconf 18 talk](https://www.youtube.com/watch?v=U1kSAELCBDw&list=PL81sUbsFNc5ZzhVxTZJqeHG24iwzKL0ei&index=29).

### Download

Download Terraform 0.12 according your architecture
```
https://releases.hashicorp.com/terraform/0.12.0-alpha2/
```


### Use 
* unzip `terraform-0.12-alpha2`
* Add your aws.tfvars file containing `aws_access_key` and `aws_secrety_key` to file like `aws.tfvars` 
* Run from specific directory (for example `security_groups`)
```bash
./terraform init
./terraform plan -var-file=aws.tfvars  -var-file=security_groups.tfvars
./terraform apply -var-file=aws.tfvars  -var-file=security_groups.tfvars
```

### Simple example with Terraform using AWS provider
  
 `
 # Configure the AWS Provider
provider "aws" {
  region  = "us-east-1"
  shared_credentials_file = "/home/user/.aws/credentials"
  profile = "awsterraform"
}
resource "aws_instance" "new-test-aws-instance" {
  ami = "ami-00a208c7cdba991ea"
  instance_type = "t2.micro"
}
`
