Terraform Module for creating Global Accelerator resources on Alibaba Cloud.

terraform-alicloud-global-accelerator
=====================================================================

English | [简体中文](README-CN.md)

This module is used to create a Global Accelerator under Alibaba Cloud.

These types of resources are supported:

* [alicloud_ga_accelerator](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/ga_accelerator)
* [alicloud_ga_bandwidth_package](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/ga_bandwidth_package)
* [alicloud_ga_bandwidth_package_attachment](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/ga_bandwidth_package_attachment)
* [alicloud_ga_endpoint_group](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/ga_endpoint_group)
* [alicloud_ga_listener](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/ga_listener)

## Usage

```hcl
module "example" {
  source                              = "terraform-alicloud-modules/global-accelerator/alicloud"
  #alicloud_ga_accelerator
  create_accelerator                  = true
  accelerator_name                    = "tf-test"
  pricing_cycle                       = "Month"
  accelerator_spec                    = "1"
  #alicloud_ga_bandwidth_package
  create_bandwidth_package            = true
  bandwidth_package_name              = "tf-test"
  bandwidth                           = 20
  bandwidth_package_type              = "Basic"
  payment_type                        = "Subscription"
  billing_type                        = "PayByTraffic"
  ratio                               = 40
  create_bandwidth_package_attachment = true 
  #alicloud_ga_listener
  create_listener                     = true
  listener_name                       = "tf-test"
  port_ranges                         = {
    from_port = 60
    to_port   = 70
  }
  #alicloud_ga_endpoint_group
  create_endpoint_group               = true
  endpoint_group_name                 = "tf-test"
  endpoint_group_region               = "cn-hangzhou"
  endpoint_configurations             = {
    weight   = "20"
    type     = "PublicIp"
    endpoint = "114.23.00.xx"
  }
}
```

## Examples

* [complete example](https://github.com/terraform-alicloud-modules/terraform-alicloud-global-accelerator/tree/main/examples/complete)

## Notes

* This module using AccessKey and SecretKey are from `profile` and `shared_credentials_file`. If you have not set them
  yet, please install [aliyun-cli](https://github.com/aliyun/aliyun-cli#installation) and configure it.

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | > = 0.13.0 |
| <a name="requirement_alicloud"></a> [alicloud](#requirement\_alicloud) | > = 1.150.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_alicloud"></a> [alicloud](#provider\_alicloud) | > = 1.150.0 |

## Submit Issues

If you have any problems when using this module, please opening
a [provider issue](https://github.com/aliyun/terraform-provider-alicloud/issues/new) and let us know.

**Note:** There does not recommend opening an issue on this repo.

## Authors

Created and maintained by Alibaba Cloud Terraform Team(terraform@alibabacloud.com).

## License

MIT Licensed. See LICENSE for full details.

## Reference

* [Terraform-Provider-Alicloud Github](https://github.com/aliyun/terraform-provider-alicloud)
* [Terraform-Provider-Alicloud Release](https://releases.hashicorp.com/terraform-provider-alicloud/)
* [Terraform-Provider-Alicloud Docs](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs)
