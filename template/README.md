{% assign split = os-arch | split: "-" -%}
{% assign os = split[0] -%}
# How to build

To build the extension, run the following command:

```bash
cargo build
```

# How to run the extension

To run the extension, run the following command:

```bash
{% if os == "macos" -%}
php -d extension=./target/debug/{{crate_name}}.dylib test.php
{% elsif os == "linux" %}
php -d extension=./target/debug/{{crate_name}}.so test.php
{% elsif os == "windows" %}
php -d extension=./target/debug/{{crate_name}}.dll test.php
{% endif -%}
```