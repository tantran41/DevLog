# Enums
	- enums are basically just numbers. In this instance
	- `FICTION = 0` and `NONFICTION = 1`
	-
	  ```c++
	  enum BookType {FICTION,NONFICTION};
	  ```
	- `bookTypeStrings` are really just [[C++ Include string|string]] labels for the `BookType` enum as the enum in really is just numbers.
	-
	  ```c++
	  static const std::string bookTypeStrings[] = {"FICTION","NONFICTION"};
	  ```
	- The enumumerated values are being used as an index for the label values:
	-
	  ```c++
	  bookTypeStrings[FICTION] // returns the string: "FICTION"
	  bookTypeStrings[NONFICTION] // returns the string: "NONFICTION"
	  ```
	- The order of the strings does matter in this instance as the values default to a normal 0..1..n indexing unless manually set to specific values:
	-
	  ```c++
	  enum light { RED = 2, YELLOW = 5, GREEN = 7 };
	  ```