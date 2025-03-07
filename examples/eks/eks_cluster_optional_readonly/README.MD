# Example of EKS cluster connected to CAST AI to read-only mode with ability to switch cluster to full access mode.
Following example creates EKS cluster and its supporting resources using AWS community modules.
After EKS cluster is created, by default it is onboarded to CAST AI in Read-only mode.
Read-only behaviour is controlled by bool variable `readonly`.
Example configuration should be analysed in the following order:
1. Create VPC - `vpc.tf`
2. Create EKS cluster - `eks.tf`
3. Create IAM resources required for CAST AI full access mode to manage the cluster - `iam.tf`
4. Create CAST AI related resources to connect EKS cluster to CAST AI in read-only mode - `castai.tf`

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

# Enable full access mode after cluster was already onboarded to read-only mode
1. Set variable `readonly = false` and run `terraform apply -var-file=tf.vars`

Note: Current provider version (v3.13.0) does not support `castai_eks_cluster` resource in-place re-creation.
If `castai_eks_cluster` have to be re-created follow the steps below:
1. Delete cluster using [/DeleteCluster](https://api.cast.ai/v1/spec/#/ExternalClusterAPI/ExternalClusterAPIDeleteCluster) API call.
If cluster was already onboarded to full access mode, and you don't want to delete CAST AI created K8s nodes, make sure that `castai_eks_cluster` parameter is set to `delete_nodes_on_disconnect = false`.
2. Run `terraform apply -var-file=tf.vars`

