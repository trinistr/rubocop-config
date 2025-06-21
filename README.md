# rubocop-config

My [RuboCop](https://rubygems.org/gems/rubocop) configuration to be shared between different projects.

Similar in spirit to [rubocop-rails-omakase](https://github.com/rails/rubocop-rails-omakase),
but with actual rules and style.

This configuration is somewhat opinionated and does not always conform to Ruby style guide.
It will also probably change over time.

Currently contains configuration for:
- [rubocop](https://github.com/rubocop/rubocop)
- [rubocop-performance](https://github.com/rubocop/rubocop-performance)
- [rubocop-rspec](https://github.com/rubocop/rubocop-rspec)

> [!TIP]
> Recommended extra plugins:
> - [rubocop-packaging](https://github.com/utkarsh2102/rubocop-packaging)
> - [rubocop-rake](https://github.com/rubocop/rubocop-rake)
> - [rubocop-thread_safety](https://github.com/rubocop/rubocop-thread_safety)
>
> Even more extra for Rails projects:
> - [rubocop-capybara](https://github.com/rubocop/rubocop-capybara)
> - [rubocop-factory_bot](https://github.com/rubocop/rubocop-factory_bot)
> - [rubocop-rails](https://github.com/rubocop/rubocop-rails)
> - [rubocop-rspec_rails](https://github.com/rubocop/rubocop-rspec_rails)

## Usage

Puts this in your `.rubocop.yml` (custom file locations are not supported):
```yaml
inherit_from:
  - https://raw.githubusercontent.com/trinistr/rubocop-config/main/rubocop.yml

plugins:
  - rubocop-performance
  - rubocop-rspec
  # ...other plugins
# require:
#  # older plugins

# Your configuration goes here
```

RuboCop will download the configuration from GitHub and cache it locally.
When the configuration changes, RuboCop will download the new version automatically.

> [!NOTE]
> The plugin system is supported in RuboCop 1.72+. In earlier versions, use `require` instead of `plugins`.

<details>
<summary>Why is `.rubocop.yml` required?</summary>

RuboCop fails on at least some cops if they are configured, but the plugins are not loaded.
As ERB preprocessing happens on file load, before we can determine the full configuration,
we have to manually check a known file to determine what cops to enable.

Sadly, this means that additional plugins' activation in subfolders will not influence
what is loaded in this configuration.
</details>

## Gems' versions

This configuration was originally written based on these versions:
- rubocop (1.72.2)
- rubocop-performance (1.24.0)
- rubocop-rspec (3.5.0)

However, the only hard requirement is `"rubocop", "~> 1.0"`.
All cops introduced later, and all plugins' cops are protected by version checks.
Later versions of gems will probably work, unless a major version changes cops too much.

## Additional configuration

Using all or any of RuboCop plugins is not required, you can just not include them in your config.
All plugin cops' configurations are surrounded with a `grep` test, so they won't activate if the plugin is not included.

Cop settings can be overridden as usual, see [RuboCop Configuration](https://docs.rubocop.org/rubocop/configuration.html), especially [inheritance](https://docs.rubocop.org/rubocop/configuration.html#inheritance) section for details.

## Other interesting plugins

All rubocop gems can be found at [RubyGems](https://rubygems.org/search?query=rubocop).
Official plugins are available under [rubocop organization on GitHub](https://github.com/orgs/rubocop/repositories).

These are plugins I found interesting and worth considering:
- [rubocop-config-prettier](https://github.com/xinminlabs/rubocop-config-prettier)
- [rubocop-md](https://github.com/rubocop/rubocop-md)
- [rubocop-obsession](https://github.com/jeromedalbert/rubocop-obsession)
- [rubocop-yard](https://github.com/ksss/rubocop-yard)
