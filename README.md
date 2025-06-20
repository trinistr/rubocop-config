# rubocop-config

My [RuboCop](https://rubygems.org/gems/rubocop) configuration to be shared between different projects.

This configuration is somewhat opinionated and does not always conform to Ruby style guide.
It will also probably change over time.

Currently contains configuration for:
- rubocop
- rubocop-performance
- rubocop-rspec

## Usage

Puts this in your `.rubocop.yml` (custom file locations are not supported):
```yaml
inherit_from:
  - https://raw.githubusercontent.com/trinistr/rubocop-config/main/rubocop.yml

# `require:` before rubocop 1.72
plugins:
  - rubocop-performance
  - rubocop-rspec
  # ...other plugins

# Your configuration here
```

RuboCop will download the configuration from GitHub and cache it locally.
When the configuration changes, RuboCop will download the new version automatically.

## Gems' versions

This configuration was originally written based on these versions:
- rubocop (1.72.2)
- rubocop-performance (1.24.0)
- rubocop-rspec (3.5.0)

Later versions should probably work (unless a major version changes cops), previous versions probably will work too.

## Configuration

Using all or any of RuboCop plugins is not required, you can just not include them in your config.
All plugin cops' configurations are surrounded with a `grep` test, as RuboCop does not like unknown cop configurations (this creates a requirement for a root `.rubocop.yml` file).

Cop settings can be overridden as usual, see [RuboCop Configuration](https://docs.rubocop.org/rubocop/configuration.html), especially [inheritance](https://docs.rubocop.org/rubocop/configuration.html#inheritance) section for details.
