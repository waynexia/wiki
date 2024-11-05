- Use another `addr2line` implementation.
-
- Build:
- ```shell
  git clone https://github.com/gimli-rs/addr2line
  cd addr2line
  cargo build --release --bin addr2line --features=bin
  ```
- And add `target/release` to `PATH` like
- ```shell
  PATH=/home/wayne/repo/addr2line/target/release:$PATH perf report
  ```
-