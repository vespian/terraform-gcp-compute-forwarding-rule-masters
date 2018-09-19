GCP Forwarding Rule - Masters
============
This module creates an GCP forwarding rule for DC/OS masters. The default ports are `80` and `443`. Also a default healthcheck is applied.

EXAMPLE
-------

```hcl
module "dcos-forwarding-rule-masters" {
  source  = "terraform-dcos/compute-forwarding-rule-masters/gcp"
  version = "~> 0.1"

  name_prefix = "production"

  masters_self_link = [${"module.masters.instances_self_link"}]
}
```


## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| additional_rules | Additional list of rules. These Rules are an additon to the default rules. | string | `<list>` | no |
| masters_self_link | List of master instances self links | list | `<list>` | no |
| name_format | printf style format for naming the ELB. Gets truncated to 32 characters. (input cluster_name) | string | `%s-master-forwarding-rule` | no |
| name_prefix | Cluster Name | string | - | yes |

## Outputs

| Name | Description |
|------|-------------|
| ip_address | IP Address of master load balancer |
