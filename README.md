# binary-writer-and-reader
- This is a small i've created just for fun because i dunno what to do at home, and i'm kinda stressed. You can understand and use it easily because there's no complex task or something in it. i didn't test the code, because i'm lazy, just straight up write it and post it as my first **Github** project. Make an issues if you found any bug or memory-leak.

## + Quick Guide:

**binary writer usage:**
```cpp
int main(int argc, char* argv[])
{
	using namespace utility;
	binary_writer* buffer = new binary_writer(0x100);
	buffer->set_string("I'm Glsswrks");
	buffer->set_float(1.83); // my height ^-^

	// cleanup function not really neccesary
	// only call if you want to free the memory instantly
	buffer->cleanup();
	delete buffer;

	return EXIT_SUCCESS;
}
```

**binary reader usage:**
```cpp
int main(int argc, char* argv[])
{
	using namespace utility;
	binary_writer* buffer = new binary_writer(0x100);
	buffer->set_string("I'm Glsswrks");
	buffer->set_float(1.83);

	// assume that we want to read from this block of memory
	// we pass the pointer to the memory block and its size
	binary_reader br = binary_reader(
		buffer->get(), buffer->size()
	);

	_STD string name = br.get_string();
	float height = br.get_float();

	std::println(_STD cout, "name: {}, height: {}", name, height);
	// the result will be: "name: I'm Glsswrks, height: 1.83"

	return EXIT_SUCCESS;
}
```
