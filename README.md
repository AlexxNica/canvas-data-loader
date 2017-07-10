# Canvas Data Loader #

This is the source code for the Canvas Data Loader. The Canvas Data Loader is an example application
that downloads your data, and imports it into a Database. The process is completely automated, and is
able to handle things like Historical Refreshes, Schema Changes, and the 24-36 hour variance all without
issue.

It should be noted although there are better options out there, there isn't a reason why you couldn't use
the loader to handle all of your imports everyday. The Canvas Data Loader could for example handle your
imports at first, and then later off be handed to a more stable process.

## How Do I Use It? ##

The following instructions are for a linux server, but steps 1-5 should work universally.
You'll just need to use your systems way of scheduling a repeating task instead of crons if you
are not using linux.

1. Clone this repository.
2. Copy the default configuration, and modify it to your needs:
  * `cp ./config/default.toml ./config/local.toml`
  * `my_text_editor ./config/local.toml`
3. Choose a home for the importer, and copy this repository there.
4. [Install Rust](https://www.rust-lang.org/en-US/install.html)
5. Build a release version: `cargo build --release`.
6. Setup a crontab to run the importer every hour:
  * `crontab -e`
  * Enter on it's own line, replacing the path to your importer: `0 * * * * cd <my_cdl_location> && RUST_LOG=info ./target/release/cdl-runner > /var/log/cdl-log 2>&1`
7. Tadah!

## License ##

The Canvas Data Loader is Licensed under MIT.
