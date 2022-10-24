title:: compile_command.json file for ccls

- Sometimes `ccls` cannot find path/settings in complex project. It will need a `compile_command.json` to specify those things.
- ```bash
  cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=1
  ```
-