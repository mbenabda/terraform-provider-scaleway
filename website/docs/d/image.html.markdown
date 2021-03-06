---
layout: "scaleway"
page_title: "Scaleway: scaleway_image"
description: |-
  Get information on a Scaleway image.
---

# scaleway_image

**DEPRECATED**: This resource is deprecated and will be removed in `v2.0+`.
Please use `scaleway_instance_image` instead or `scaleway_marketplace_image_beta` depending on your usage.

Use this data source to get the ID of a registered Image for use with the
`scaleway_server` resource.

## Example Usage

```hcl
data "scaleway_image" "ubuntu" {
  architecture = "arm"
  name         = "Ubuntu Precise"
}

resource "scaleway_server" "base" {
  name  = "test"
  image = data.scaleway_image.ubuntu.id
  type  = "C1"
}
```

## Argument Reference

* `architecture` - (Required) any supported Scaleway architecture, e.g. `x86_64`, `arm`

* `name_filter` - (Optional) Regexp to match Image name by

* `name` - (Optional) Exact name of desired Image

* `most_recent` - (Optional) Return most recent image if multiple exist. Can not be used together with name_filter.

## Attributes Reference

`id` is set to the ID of the found Image. In addition, the following attributes
are exported:

* `architecture` - architecture of the Image, e.g. `arm` or `x86_64`

* `organization` - uuid of the organization owning this Image

* `public` - is this a public image

* `creation_date` - date when image was created
