---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "castai_node_template Resource - terraform-provider-castai"
subcategory: ""
description: |-
  CAST AI node template resource to manage node templates
---

# castai_node_template (Resource)

CAST AI node template resource to manage node templates



<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Name of the node template.

### Optional

- `cluster_id` (String) CAST AI cluster id.
- `configuration_id` (String) CAST AI node configuration id to be used for node template.
- `constraints` (Block List, Max: 1) (see [below for nested schema](#nestedblock--constraints))
- `custom_instances_enabled` (Boolean) Marks whether custom instances should be used when deciding which parts of inventory are available. Custom instances are only supported in GCP.
- `custom_instances_with_extended_memory_enabled` (Boolean) Marks whether custom instances with extended memory should be used when deciding which parts of inventory are available. Custom instances are only supported in GCP.
- `custom_labels` (Map of String) Custom labels to be added to nodes created from this template.
- `custom_taints` (Block List) Custom taints to be added to the nodes created from this template. `shouldTaint` has to be `true` in order to create/update the node template with custom taints. If `shouldTaint` is `true`, but no custom taints are provided, the nodes will be tainted with the default node template taint. (see [below for nested schema](#nestedblock--custom_taints))
- `is_default` (Boolean) Flag whether the node template is default.
- `is_enabled` (Boolean) Flag whether the node template is enabled and considered for autoscaling.
- `rebalancing_config_min_nodes` (Number) Minimum nodes that will be kept when rebalancing nodes using this node template.
- `should_taint` (Boolean) Marks whether the templated nodes will have a taint.
- `timeouts` (Block, Optional) (see [below for nested schema](#nestedblock--timeouts))

### Read-Only

- `id` (String) The ID of this resource.

<a id="nestedblock--constraints"></a>
### Nested Schema for `constraints`

Optional:

- `architectures` (List of String) List of acceptable instance CPU architectures, the default is amd64. Allowed values: amd64, arm64.
- `compute_optimized` (Boolean) Compute optimized instance constraint - will only pick compute optimized nodes if true.
- `enable_spot_diversity` (Boolean) Enable/disable spot diversity policy. When enabled, autoscaler will try to balance between diverse and cost optimal instance types.
- `fallback_restore_rate_seconds` (Number) Fallback restore rate in seconds: defines how much time should pass before spot fallback should be attempted to be restored to real spot.
- `gpu` (Block List, Max: 1) (see [below for nested schema](#nestedblock--constraints--gpu))
- `instance_families` (Block List, Max: 1) (see [below for nested schema](#nestedblock--constraints--instance_families))
- `is_gpu_only` (Boolean) GPU instance constraint - will only pick nodes with GPU if true
- `max_cpu` (Number) Max CPU cores per node.
- `max_memory` (Number) Max Memory (Mib) per node.
- `min_cpu` (Number) Min CPU cores per node.
- `min_memory` (Number) Min Memory (Mib) per node.
- `on_demand` (Boolean) Should include on-demand instances in the considered pool.
- `os` (List of String) List of acceptable instance Operating Systems, the default is linux. Allowed values: linux, windows.
- `spot` (Boolean) Should include spot instances in the considered pool.
- `spot_diversity_price_increase_limit_percent` (Number) Allowed node configuration price increase when diversifying instance types. E.g. if the value is 10%, then the overall price of diversified instance types can be 10% higher than the price of the optimal configuration.
- `spot_interruption_predictions_enabled` (Boolean) Enable/disable spot interruption predictions.
- `spot_interruption_predictions_type` (String) Spot interruption predictions type. Can be either "aws-rebalance-recommendations" or "interruption-predictions".
- `storage_optimized` (Boolean) Storage optimized instance constraint - will only pick storage optimized nodes if true
- `use_spot_fallbacks` (Boolean) Spot instance fallback constraint - when true, on-demand instances will be created, when spots are unavailable.

<a id="nestedblock--constraints--gpu"></a>
### Nested Schema for `constraints.gpu`

Optional:

- `exclude_names` (List of String) Names of the GPUs to exclude.
- `include_names` (List of String) Instance families to include when filtering (excludes all other families).
- `manufacturers` (List of String) Manufacturers of the gpus to select - NVIDIA, AMD.
- `max_count` (Number) Max GPU count for the instance type to have.
- `min_count` (Number) Min GPU count for the instance type to have.


<a id="nestedblock--constraints--instance_families"></a>
### Nested Schema for `constraints.instance_families`

Optional:

- `exclude` (List of String) Instance families to include when filtering (excludes all other families).
- `include` (List of String) Instance families to exclude when filtering (includes all other families).



<a id="nestedblock--custom_taints"></a>
### Nested Schema for `custom_taints`

Required:

- `key` (String) Key of a taint to be added to nodes created from this template.

Optional:

- `effect` (String) Effect of a taint to be added to nodes created from this template, the default is NoSchedule. Allowed values: NoSchedule, NoExecute.
- `value` (String) Value of a taint to be added to nodes created from this template.


<a id="nestedblock--timeouts"></a>
### Nested Schema for `timeouts`

Optional:

- `create` (String)
- `delete` (String)
- `read` (String)
- `update` (String)

## Import

Import is supported using the following syntax:

```shell
# Import node template by specifying cluster ID and node template name.
terraform import castai_node_template.default_by_castai 105e6fa3-20b1-424e-v589-9a64d1eeabea/default-by-castai
```
