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

<!-- BEGIN_TF_DOCS -->
## Requirements

No requirements.

## Providers

| Name | Version |
|------|---------|
| <a name="provider_google"></a> [google](#provider\_google) | n/a |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [google_folder_organization_policy.folder_policy_boolean](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/folder_organization_policy) | resource |
| [google_folder_organization_policy.folder_policy_list_allow_all](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/folder_organization_policy) | resource |
| [google_folder_organization_policy.folder_policy_list_allow_values](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/folder_organization_policy) | resource |
| [google_folder_organization_policy.folder_policy_list_deny_all](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/folder_organization_policy) | resource |
| [google_folder_organization_policy.folder_policy_list_deny_values](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/folder_organization_policy) | resource |
| [google_folder_organization_policy.folder_policy_list_exclude_folders](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/folder_organization_policy) | resource |
| [google_folder_organization_policy.policy_boolean_exclude_folders](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/folder_organization_policy) | resource |
| [google_organization_policy.org_policy_boolean](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/organization_policy) | resource |
| [google_organization_policy.org_policy_list_allow_all](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/organization_policy) | resource |
| [google_organization_policy.org_policy_list_allow_values](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/organization_policy) | resource |
| [google_organization_policy.org_policy_list_deny_all](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/organization_policy) | resource |
| [google_organization_policy.org_policy_list_deny_values](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/organization_policy) | resource |
| [google_project_organization_policy.policy_boolean_exclude_projects](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/project_organization_policy) | resource |
| [google_project_organization_policy.project_policy_boolean](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/project_organization_policy) | resource |
| [google_project_organization_policy.project_policy_list_allow_all](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/project_organization_policy) | resource |
| [google_project_organization_policy.project_policy_list_allow_values](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/project_organization_policy) | resource |
| [google_project_organization_policy.project_policy_list_deny_all](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/project_organization_policy) | resource |
| [google_project_organization_policy.project_policy_list_deny_values](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/project_organization_policy) | resource |
| [google_project_organization_policy.project_policy_list_exclude_projects](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/project_organization_policy) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_allow"></a> [allow](#input\_allow) | (Only for list constraints) List of values which should be allowed | `list(string)` | <pre>[<br>  ""<br>]</pre> | no |
| <a name="input_allow_list_length"></a> [allow\_list\_length](#input\_allow\_list\_length) | The number of elements in the allow list | `number` | `0` | no |
| <a name="input_constraint"></a> [constraint](#input\_constraint) | The constraint to be applied | `string` | n/a | yes |
| <a name="input_deny"></a> [deny](#input\_deny) | (Only for list constraints) List of values which should be denied | `list(string)` | <pre>[<br>  ""<br>]</pre> | no |
| <a name="input_deny_list_length"></a> [deny\_list\_length](#input\_deny\_list\_length) | The number of elements in the deny list | `number` | `0` | no |
| <a name="input_enforce"></a> [enforce](#input\_enforce) | If boolean constraint, whether the policy is enforced at the root; if list constraint, whether to deny all (true) or allow all | `bool` | `null` | no |
| <a name="input_exclude_folders"></a> [exclude\_folders](#input\_exclude\_folders) | Set of folders to exclude from the policy | `set(string)` | `[]` | no |
| <a name="input_exclude_projects"></a> [exclude\_projects](#input\_exclude\_projects) | Set of projects to exclude from the policy | `set(string)` | `[]` | no |
| <a name="input_folder_id"></a> [folder\_id](#input\_folder\_id) | The folder id for putting the policy | `string` | `null` | no |
| <a name="input_organization_id"></a> [organization\_id](#input\_organization\_id) | The organization id for putting the policy | `string` | `null` | no |
| <a name="input_policy_for"></a> [policy\_for](#input\_policy\_for) | Resource hierarchy node to apply the policy to: can be one of `organization`, `folder`, or `project`. | `string` | n/a | yes |
| <a name="input_policy_type"></a> [policy\_type](#input\_policy\_type) | The constraint type to work with (either 'boolean' or 'list') | `string` | `"list"` | no |
| <a name="input_project_id"></a> [project\_id](#input\_project\_id) | The project id for putting the policy | `string` | `null` | no |

## Outputs

No outputs.
<!-- END_TF_DOCS -->