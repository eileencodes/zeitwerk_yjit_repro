# README

To repro yjit issue:

* I added `Rails.autoloaders.log` to the config/application.rb
* Boot the server with `RUBY_YJIT_ENABLE=1 bin/rails s`
* The server crashes with

```
thread '<unnamed>' panicked at 'assertion failed: ctx.get_stack_size() == 1', ./yjit/src/codegen.rs:6294:5
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
YJIT panicked while holding VM lock acquired at ./yjit/src/core.rs:1694. Aborting...
```

This is not reproducible without autoloaders log and it is not reproducible without YJIT.
