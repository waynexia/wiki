- regex
  ```
  \x1b\[[0-9;]*m
  ```
- sed
  ```shell
  sed -e 's/\x1b\[[0-9;]*m//g'
  ```
-