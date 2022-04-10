
[![Rust](https://github.com/aramnhammer/environ/actions/workflows/rust.yml/badge.svg?branch=main)](https://github.com/aramnhammer/environ/actions/workflows/rust.yml)

# environ
Simple environment loader/setter that loads desired env variables from a file and inserts them into the runtime environment.

## use cases
Running an application that relies on environment variables locally by simply having those variables in a file instead of setting your system environment every time, like so:

```
let config_path = "config/server.env";
match metadata(config_path) {
    Ok(_) => environ::EnvironmentLoader::new(config_path),
    Err(_) => info!("Using system environment"),
}
```
Here we load the config file if it exists, otherwise we default to system environment variables (like docker). This makes it easy to switch between debugging locally on your machine (by loading some preset file `config/server.env`), and some production environment.