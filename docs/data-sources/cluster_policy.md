---
subcategory: "Compute"
---

# databricks_cluster_policy Data Source

-> **Note** If you have a fully automated setup with workspaces created by [databricks_mws_workspaces](../resources/mws_workspaces.md) or [azurerm_databricks_workspace](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/databricks_workspace), please make sure to add [depends_on attribute](../index.md#data-resources-and-authentication-is-not-configured-errors) in order to prevent _authentication is not configured for provider_ errors.

Retrieves information about [databricks_cluster_policy](../resources/cluster_policy.md).

## Example Usage

Referring to a cluster policy by name:

```hcl
data "databricks_cluster_policy" "personal" {
  name = "Personal Compute"
}

resource "databricks_cluster" "my_cluster" {
  policy_id = data.databricks_cluster_policy.personal.id
  ...
}
```

## Argument Reference

Data source allows you to pick a cluster policy by the following attribute

- `name` - Name of the cluster policy. The cluster policy must exist before this resource can be planned.

## Attribute Reference

Data source exposes the following attributes:

- `id` - The id of the cluster policy.
* `definition` - Policy definition: JSON document expressed in [Databricks Policy Definition Language](https://docs.databricks.com/administration-guide/clusters/policies.html#cluster-policy-definition).

