![Coalfire](coalfire_logo.png)


# Google Cloud Organization Policy Terraform Module

## Description

This Terraform module makes it easier to manage organization policies for your Google Cloud environment, particularly when you want to have exclusion rules. This module will allow you to set a top-level org policy and then disable it on individual projects or folders easily. Coalfire has tested this module with Terraform version 1.5.0 and the Hashicorp Google provider versions 4.70 - 5.0.

FedRAMP Compliance: High (included as a part of Identity & Access Management)

### Usage

```
module "organization_policies_type_boolean" {
  source = "github.com/Coalfire-CF/terraform-gcp-org-policy"

  for_each = toset(var.boolean_type_organization_policies)

  organization_id = var.org_id
  policy_for      = "organization"
  policy_type     = "boolean"
  enforce         = "true"
  constraint      = "constraints/${each.value}"
}
```

