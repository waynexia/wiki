- *credit to github.com/discord9*
- Save this script. Assume the file name is `stack-size.py`.
- ```python
  import gdb
  
  
  # Define a GDB command
  class PrintStackSizes(gdb.Command):
      """Print stack sizes of all functions in the current backtrace"""
  
      def __init__(self):
          super(PrintStackSizes, self).__init__("print-stack-sizes", gdb.COMMAND_USER)
  
      def invoke(self, arg, from_tty):
          # Get current frame
          frame = gdb.selected_frame()
          if not frame:
              print("No frame selected.")
              return
  
          # Walk frame and collect info
          frame_sizes = []
          while frame:
              # Switch to the current frame
              gdb.execute(f"frame {frame.level()}")
              # Get stack pointer
              sp_value = gdb.parse_and_eval("$sp")
              # Save the function name and stack pointer value
              frame_sizes.append((frame.name(), sp_value))
              # Step next
              frame = frame.older()
  
          sum = 0
          # Compute and print the stack size of each function
          for i in range(len(frame_sizes) - 1):
              func_name, sp_value = frame_sizes[i]
              next_sp_value = frame_sizes[i + 1][1]
              stack_size = next_sp_value - sp_value
              if stack_size > 0 and stack_size < 2048 * 1024:
                  sum += stack_size
              print(f"Function: {func_name}, Stack Size: {stack_size}, i: {i}")
  
          print(f"Sum: {sum}")
  
  
  # Register the command
  PrintStackSizes()
  ```
- In `gdb`, type
	- ```
	  source stack-size.py
	  ```
- And then invoke this function by
	- ```
	  print-stack-sizes
	  ```
-
-