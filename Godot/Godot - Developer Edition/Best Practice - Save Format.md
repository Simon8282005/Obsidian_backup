### Allow player to read and edit the save data

如果想让玩家能够更改数据，那么就要使用 text-based 的方式来存储数据

### Don't allow player to read and edit data

### 那就用 binary files

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

### JSON

最容易看的 file，但同时体积也比较大，160 bytes，对比 binary 的 42 bytes

```python
```json
[
  {
    "age": 50,
    "character_name": "Larry",
    "position": {
      "x": 120.046242,
      "y": 119.111282
    }
  },
  {
    "age": 25,
    "character_name": "Harry",
    "position": {
      "x": 211.275574,
      "y": 108.217361
    }
  }
]
```

要生成 JSON 的代码也比较短

```python
## Exports relevant class data in a dictionary that will be converted into a JSON
## format by by the saving class. The variable names match to make it easier to
## read and load later.
func export_to_dict() -> Dictionary:
	return {
		"age": age,
		"character_name": character_name,
		"position": {"x": position.x, "y": position.y}  # 数据被分开了
	}


## Imports relevant class data from a dictionary that was loaded from JSON data.
func import_from_dict(dict: Dictionary) -> void:
	age = dict.age
	character_name = dict.character_name
	position.x = dict.position.x
	position.y = dict.position.y
```

使用 `parse()` 来加载数据

```python
const SAVE_JSON := "user://save.json"

## The saving class' method for saving a file to JSON.
func save_json() -> void:
	# Gather each dictionary from each children to save into a single array
	var output := []
	for child in get_children():
		output.push_back(child.export_to_dict())

	# Convert the array, and its dictionaries, using the `JSON` singleton
	# into a block of JSON. Note the second parameter that specifies how to
	# indent the file. Without this parameter, the JSON would be on a single line.
	var json := JSON.print(output, "  ")

	# Save the resulting JSON to a file using the `File` class in write mode
	var file := File.new()
	file.open(SAVE_JSON, File.WRITE)

	# Since our JSON is indented, we can store the entire string in one call.
	file.store_string(json)

	# Clean up
	file.close()


## The saving class' method for loading a file to JSON and spreading the data
## back to its children.
func load_json() -> void:
	# Load the file using the `File` class in read mode. Report an error if the
	# file is missing or cannot be opened.
	var file := File.new()
	var error := file.open(SAVE_JSON, File.READ)

	if not error == OK:
		print_error("Could not load file at %s" % SAVE_JSON)
		return

	# Get the array of dictionaries from the file. Note that we load the entire
	# file with get_as_text because our JSON is on multiple lines.
	var input := file.get_as_text()

	# Clean up
	file.close()

	# Use the JSON singleton to parse the string into an array of dictionaries.
	# JSON.parse returns JSONParseResult, in case of errors, and the actual
	# array is in the `result` property.
	var json: Array = JSON.parse(input).result

	# In the same order as they were saved, we iterate over each child and
	# provide the dictionary from that part of the array.
	for i in get_child_count():
		get_child(i).import_from_dict(json[i])
```

### 折中的办法

数据的体积是 77 bytes，比 binary 大，但比 json 小

Godot 有内置了两个库，分别是 `var2str`（用来导出） 和 `str2var` （用来加载）

比 binary 容易看，也没有 JSON 的体积那么大，岂不美哉

```json
50
"Larry"
Vector2( 120.206, 119.449 )
25
"Harry"
Vector2( 211.11, 107.883 )
```

数据是一行一行储存的，也是一行一行加载的

```python
## Export the class' relevant data as Godot-recognized data lines of strings
## Each piece of data is saved in order as a line using `var2str` so Godot
## can load it later.
func save_to_var(file: File) -> void:
	file.store_line(var2str(age))
	file.store_line(var2str(character_name))
	file.store_line(var2str(position))


## Import the class' relevant data from data lines of strings.
## Each piece of data is loaded in as a line, then run through the `str2var` to
## turn it back into data. Must load in the same order it was saved in.
func load_from_var(file: File) -> void:
	age = str2var(file.get_line())
	character_name = str2var(file.get_line())
	position = str2var(file.get_line())
```

调用也是三个里面最简单的了

```python
const SAVE_VAR := "user://sav1.sav"

## The save class' method to prompt its children to save their data to a file.
func save_var() -> void:
	# Instances a new `File` in write mode and iterate over each child to use it
	# to save.
	var file := File.new()
	file.open(SAVE_VAR, File.WRITE)

	for child in get_children():
		child.save_to_var(file)

	# Clean up
	file.close()


func load_var() -> void:
	# Instances a new `File` in read mode and attempt to load the file, if it is
	# open-able and readable.
	var file := File.new()
	var error := file.open(SAVE_VAR, File.READ)

	if not error == OK:
		print_error("Could not load file at %s" % SAVE_VAR)
		return

	# Send the loaded file to each child in the same order they were saved to
	# have them load their data.
	for child in get_children():
		child.load_from_var(file)

	# Clean up
	file.close()  # flush() 自动运行
```