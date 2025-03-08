# 4640-w9-lab-start-w25

See lab instructions on D2L

1. **SSH Key**: Generate an SSH key pair to use with your EC2 instance:

   ```bash
   ssh-keygen -t ed25519 -f ~/.ssh/4640-lab09 -C "4640-lab09-ansible"
   ```

2. **AWS Key Pair**: Use the provided `import_lab_key` script to import your public key into AWS:

   ```bash
   cd scripts/
   ./import_lab_key ~/.ssh/4640-lab09.pub
   ```

---

## Steps to Build and Deploy

### 1. Build the AMI with Packer

Navigate to the root directory and run the following commands to build the custom AMI:

```bash

packer init .
packer fmt .
packer validate . 
packer build .
```

This will create an AMI named `packer-ansible-nginx` in your AWS account.

### 2. Deploy the Infrastructure with Terraform

Navigate to the root directory and run the following commands to deploy the EC2 instance:

```bash
terraform init
terraform fmt
terraform validate
terraform plan -out 4640-lab09
terraform apply 4640-lab09
```

### 3. Destroy Terraform Resources

```bash
terraform destroy
```
