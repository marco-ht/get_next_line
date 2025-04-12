# get_next_line

This repository contains my implementation of the **get_next_line** project, developed as part of the 42 School curriculum. The objective of this project is to create a function that reads a line from a file descriptor efficiently, handling various edge cases, dynamic buffers, and supporting multiple file descriptors if necessary. This implementation serves both as an exercise in mastering file handling in C and as a demonstration of my programming capabilities.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Testing](#testing)
- [Acknowledgments](#acknowledgments)
- [Disclaimer](#disclaimer)
- [License](#license)

## Overview

The **get_next_line** project challenges you to build a function that returns the next line from a file descriptor with each call. This function must correctly manage memory, work efficiently under different conditions, and handle unexpected input gracefully. The project reinforces key concepts in C such as dynamic memory allocation, file I/O, and error handling.

## Features

- **Efficient Line Reading:** Reads one line at a time from a file descriptor.
- **Buffer Management:** Dynamically manages buffers to support varying line lengths.
- **Multi-File Descriptor Support:** Allows for simultaneous reading from multiple file descriptors.
- **Robust Error Handling:** Checks for errors such as invalid file descriptors and read failures.
- **Memory Management:** Carefully allocates and deallocates memory to prevent leaks.

## Project Structure

```
get_next_line/
├── includes/    # Header files for the get_next_line function
├── srcs/        # Source files implementing the function
├── tests/       # Test files and scripts to validate functionality
├── Makefile     # Makefile for building the project
└── README.md    # This file
```

- **includes/**: Contains header files declaring the `get_next_line` function and any necessary constants or macros.
- **srcs/**: Contains the implementation of the `get_next_line` function and its helper functions.
- **tests/**: Contains test cases and scripts to ensure the function works as intended.
- **Makefile**: Automates the build process of the project.

## Installation

To build the project, follow these steps:

1. **Clone the repository:**

   ```sh
   git clone https://github.com/yourusername/get_next_line.git
   cd get_next_line
   ```

2. **Compile the project:**

   Run the following command in your terminal:

   ```sh
   make
   ```

   This command will compile the source files and generate the necessary executable or library files.

## Usage

You can integrate and use the get_next_line function in your projects as follows:

1. Include the header file in your code:

   ```c
   #include "get_next_line.h"
   ```

2. Example usage:

   ```c
   #include <fcntl.h>
   #include <stdio.h>
   #include <stdlib.h>
   #include "get_next_line.h"

   int main(void) {
       int fd = open("example.txt", O_RDONLY);
       if (fd < 0) {
           perror("Error opening file");
           return 1;
       }

       char *line = get_next_line(fd);
       while (line) {
           printf("%s", line);
           free(line);
           line = get_next_line(fd);
       }
       close(fd);
       return 0;
   }
   ```

3. Compiling your project:

   Ensure you compile your project with the proper flags and link the required files.

## Testing

The tests/ directory includes sample files and scripts to test the functionality of get_next_line.

1. Navigate to the tests directory:

   ```sh
   cd tests
   ```

2. Run the test scripts:

   Execute the provided testing script:

   ```sh
   ./run_tests.sh
   ```

   This script will compile and run various test cases to ensure that the function performs correctly under different scenarios.

## Acknowledgments

- Special thanks to the 42 community, mentors, and peers for their continuous support and constructive feedback.
- Appreciation to the wider open-source community for the resources and discussions that enriched my learning process.

## Disclaimer

**IMPORTANT**:
This project was developed solely as part of the educational curriculum at 42 School. The code contained in this repository is published only for demonstration purposes to showcase my programming skills.

**Academic Integrity Notice**:
It is strictly prohibited to copy or present this code as your own work in any academic submissions at 42 School. Any misuse or uncredited use of this project will be considered a violation of 42 School's academic policies.

## License

This repository is licensed under the Creative Commons - NonCommercial-NoDerivatives (CC BY-NC-ND 4.0) license. You are free to share the repository as long as you:

- Provide appropriate credit.
- Do not use it for commercial purposes.
- Do not modify, transform, or build upon the material.

For further details, please refer to the CC BY-NC-ND 4.0 license documentation.

Developed with commitment and adherence to the high standards of 42 School.
