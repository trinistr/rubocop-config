# rubocop-config
My Rubocop configuration to be shared between different projects.

This configuration is somewhat opinionated and does not always conform to Ruby style guide.
It will also probably change over time.

Intended to be used with these tested versions of gems (install through `gem install` or `Gemfile`):
- rubocop (1.72.2)
- rubocop-performance (1.24.0)
- rubocop-rake (0.7.1)
- rubocop-rspec (3.5.0)
- rubocop-thread_safety (0.7.0)

## Usage

Puts this in your `.rubocop.yml` (custom file locations are not supported):
```yaml
inherit_from:
  - https://raw.githubusercontent.com/trinistr/rubocop-config/main/rubocop.yml

# `require:` before rubocop 1.72
plugins:
  - rubocop-performance
  - rubocop-rake
  - rubocop-rspec
  - rubocop-thread_safety
```

## Configuration

Using all or any of Rubocop plugins is not required, you can just not include them in your config.
All plugin cops' configurations are surrounded with a `grep` test, as Rubocop does not like unknown cop configurations (this creates a requirement for a root `.rubocop.yml` file).

Cop settings can be overridden as usual, see [Rubocop Configuration](https://docs.rubocop.org/rubocop/configuration.html) for details.
