---
layout: "launchdarkly"
page_title: "LaunchDarkly: launchdarkly_environment"
description: |-
  Create and manage LaunchDarkly environments.
---

# launchdarkly_environment

Provides a LaunchDarkly environment resource.

This resource allows you to create and manage environments in your LaunchDarkly organization.

## Example Usage

```hcl
resource "launchdarkly_environment" "staging" {
  name                 = "Staging"
  key                  = "staging"
  color                = "ff00ff"
  secure_mode          = true
  default_track_events = false
  default_ttl          = 10

  project_key = launchdarkly_project.example.key
}
```

## Argument Reference

- `project_key` - (Required) - The environment's project key.

- `name` - (Required) The name of the environment.

- `key` - (Required) The project-unique key for the environment.

- `color` - (Required) The color swatch as an RGB hex value with no leading `#`, e.g. `000000`.

- `secure_mode` - (Optional) Ensure a user of the client-side SDK cannot impersonate another user.

- `default_track_events` - (Optional) Enable data export for every flag created in this environment after `default_track_events` has been set to `true`. To learn more, read [Data Export](https://docs.launchdarkly.com/docs/data-export).

- `default_ttl` - (Optional) The TTL for the environment between 0 and 60 minutes. The TTL setting only applies to environments using the PHP SDK. To learn more, read [TTL settings](https://docs.launchdarkly.com/docs/environments#section-ttl-settings).

## Attribute Reference

In addition to the arguments above, the following attributes are exported:

- `id` - The unique environment ID in the format `project_key/environment_key`.

- `api_key` - The environment's SDK key.

- `mobile_key` - The environment's mobile key.

## Import

LaunchDarkly environments can be imported using an environment ID in the format `project_key/environment_key`, e.g.

```
$ terraform import launchdarkly_environment.staging example-project/staging
```