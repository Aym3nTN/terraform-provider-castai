# Example of EKS cluster connected to CAST AI in READ-ONLY mode
Following example creates EKS cluster and its supporting resources using AWS community modules.
After EKS cluster is created it is onboarded to CAST AI in Read-only mode.
Example configuration should be analysed in the following order:
1. Create VPC - `vpc.tf`
2. Create EKS cluster - `eks.tf`
3. Create CAST AI related resources to connect EKS cluster to CAST AI in read-only mode - `castai.tf`

# Usage
1. Rename `tf.vars.example` to `tf.vars`
2. Update `tf.vars` file with your cluster name, cluster region and CAST AI API token
3. Initialize Terraform. Under example root folder run:
```
terraform init
```
4. Run Terraform apply:
```
terraform apply -var-file=tf.vars
```
5. To destroy resources created by this example:
```
terraform destroy -var-file=tf.vars
```
