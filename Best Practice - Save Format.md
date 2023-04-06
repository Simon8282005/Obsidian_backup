### Allow player to read and edit the save data

如果想让玩家能够更改数据，那么就要使用 text-based 的方式来存储数据

### Don't allow player to read and edit data

那就用 binary files

Godot 有一个 Class 是专门处理文件储存这个部分的，那就是 Class `Files` 

![[Pasted image 20230406082551.png]]

上面一两个简单的例子，分别是储存和加载数据

可以看见不管是写入还是加载数据，第一行的代码都是要写 `var file = File.new()`，有点像 Java 了 XDD

单单是 get() 就那么多种了。。。store() 也是 XDD

![[Pasted image 20230406082323.png]]

![[Pasted image 20230406082333.png]]

为了确保数据的安全，可以用 `flush()`

> Writes the file's buffer to disk. Flushing is automatically performed when the file is closed. This means you don't need to call flush() manually before closing a file using close(). Still, calling flush() can be used to ensure the data is safe even if the project crashes instead of being closed gracefully

当一个游戏窗口被正常关掉（被 `close()` 关掉），`flush()` 会自动运行，但是如果手动呼叫 `flush()` 会更加的安全，因为就算当游戏崩溃数据还是有被储存到

```python
## Exports relevant data for a character in binary to the provided `File`. Each piece of
## data is in binary, non-human readable format.
func export_to_bin(file: File) -> void:
	# Store an integer as a 32-bit number, a value between -2,147,483,648 and 2,147,483,647
	file.store_32(age)

	# Store the length of a string as a 32-bit number. In binary, we have no way to know
	# if one byte or the next is part of a variable except by writing how many to expect.
	# The result is the number of characters to load later, followed by the string.
	file.store_32(character_name.length())
	file.store_string(character_name)

	# Store a Vector2 using its constituent X and Y parts as floating-point numbers:
	# 32-bit numbers that have a decimal number component.
	file.store_float(position.x)
	file.store_float(position.y)


## Imports the relevant class data from the provided binary `File`. Expects the
## the caret to be at the start of the data. The data must load in the same order
## it was saved in.
func import_from_bin(file: File) -> void:
	# Gets an integer from a 32-bit piece of binary data.
	age = file.get_32()

	# Gets the number of characters that make up the follow-up string, then
	# get each one as an 8-bit number - one byte - and transform it into a string
	# using the `char()` function. This uses the standardized ASCII table for the text.
	var name_length := file.get_32()
	character_name = ""
	for i in name_length:
		character_name += char(file.get_8())

	#Load a Vector2 out of its constituent X and Y parts from floating-point numbers.
	position.x = file.get_float()
	position.y = file.get_float()
```

如果要调用的话

```python
const SAVE_BINARY := "user://save.dat"

## Saves children to a binary file.
func save_binary() -> void:
	# Initializes a new `File` and opens the file in write mode, creating it
	# if it's missing.
	var file := File.new()
	file.open(SAVE_BINARY, File.WRITE)

	# For each child, pass in the handle to the file and have the child write
	# its data.
	for child in get_children():
		child.export_to_bin(file)

	# Clean up and close the file so the operating system can claim it
	file.close()


## Loads children from a binary file.
func load_binary() -> void:
	# Initializes a new `File` and open the file in read mode. If it's missing
	# or otherwise un-openable, report it as an error and return.
	var file := File.new()
	var error := file.open(SAVE_BINARY, File.READ)

	if not error == OK:
		print_error("Could not load file at %s" % SAVE_BINARY)
		return

	# Have each child import its data in the same order they were saved in.
	for child in get_children():
		child.import_from_bin(file)

	# Clean up and close the file so the operating system can claim it.
	file.close()
```




