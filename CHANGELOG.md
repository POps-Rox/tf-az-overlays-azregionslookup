# Changelog

All notable changes to this project are documented here. Format based on
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - 2026-05-11

### Changed (BREAKING)

- Upgraded `hashicorp/azurerm` provider constraint from `~> 3.116` to `~> 4.20`.
- Raised minimum Terraform CLI version from `>= 1.9` to `>= 1.10`.

### Added

- New `azure/azapi ~> 2.0` provider declaration in `versions.tf` (root, example,
  and test). Reserved for forthcoming azapi-based features and consistent with
  the rest of the POps-Rox fleet.
- New `POps-Rox/azutils ~> 1.0` (`popsrox`) provider declaration in
  `versions.tf` for parity with downstream consumers.
- `versions.tf` files added to `examples/main/` and `tests/main/` so the example
  and test stacks declare their own provider versions (previously inherited
  from the consumer).
- Comment in the example/test `provider "azurerm"` blocks noting that
  `subscription_id` is provided by the consumer via the `ARM_SUBSCRIPTION_ID`
  environment variable (required by azurerm 4.x).

### Notes

- This is a pure lookup module with no `azurerm_*` resources, so no resource
  attribute renames were required.
- CI may show transitive provider-constraint failures on example/test stacks
  until upstream POps-Rox overlays (`resourcegroup`, etc.) are also bumped to
  `~> 4.20`. Failures resolve as Phase 1 PRs land.

[2.0.0]: https://github.com/POps-Rox/terraform-az-overlays-azregionslookup/releases/tag/v2.0.0
