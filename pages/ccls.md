- `ccls` needs a `compile_command.json` file to run. see [[compile_command.json file for ccls]]
- If the project is based on `cmake`, `compile_command.json` can be generated directly
- If it's based on other things like raw `Makefile`, use `bear` to generate it:
  ```shell
  bear -- make -j
  ```
-
- Usually a project is recommended to build under `build` dir:
  ```shell
  mkdir build
  cd build
  cmake ..
  make
  ```
-