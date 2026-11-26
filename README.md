<p align="center">
  <img src="logo.jpg" alt="openCGL logo" width="420">
</p>

<h1 align="center">openCGL</h1>

<p align="center">
  A C library for testing, I/O utilities, bit operations, ternary values, strings, data structures, and error handling.
</p>

## Overview

openCGL is a header-focused C utility library organized around reusable modules for everyday systems and console programming. The project includes separate standard-C and GNU-oriented implementations for several utilities.

## Features

- Unit-test helpers and formatted test output
- Console I/O and separator utilities
- Bit operations for signed and unsigned integer types
- Binary formatting and boolean utilities
- Ternary and balanced ternary types
- String helpers
- Error and warning records
- Random-number utilities
- Dynamic data types, including arrays, stacks, queues, and dynamic storage

## Project structure

| Path | Description |
| --- | --- |
| `include/cgen/` | Public library headers |
| `include/cgen.h` | Main umbrella header |
| `src/` | Library source implementations |
| `test/` | Test programs |
| `example/` | Usage examples |
| `help/` | Markdown API notes |
| `bin/` | Compiled artifacts |
| `lib/` | Library output files |

## Getting started

### Requirements

- A C compiler that supports C11 or later
- GCC/Clang for the GNU-oriented variants
- A compatible Windows compiler for modules that use the Windows API

### Clone the repository

```bash
git clone https://github.com/Ali980-eng/openCGL.git
cd openCGL
```

### Include the library

Add the `include` directory to your compiler search path. Include the umbrella header or only the module you need:

```c
#include "cgen.h"
```

```bash
gcc -std=c11 -Iinclude your_program.c -o your_program
```

Some implementations expose GNU-prefixed APIs when `OPENCF_FOR_GNU` is defined:

```bash
gcc -std=c11 -DOPENCF_FOR_GNU -Iinclude your_program.c -o your_program
```

For source files that are not intended to use the GNU variant, do not define `OPENCF_FOR_GNU`.

## Usage example

The bit-utility header provides typed helpers for setting, resetting, retrieving, toggling, and exchanging bits.

```c
#include "cgen/bitUtilitys.h"
#include <stdint.h>
#include <stdio.h>

int main(void) {
    uint32_t value = 0u;

    value = set_u32bit(value, 3);
    printf("Bit 3: %u\n", get_u32bit(value, 3));

    value = reset_u32bit(value, 3);
    printf("Value: %u\n", value);
    return 0;
}
```

## Modules

- **Unit testing:** test records, formatted output, and equality helpers for common C types
- **I/O utilities:** separator and status-message helpers
- **Bit utilities:** count, get, set, reset, toggle, exchange, binary formatting
- **Data structures:** array, dynamic storage, stack, and queue implementations
- **Ternary:** balanced ternary representations and related operations
- **Diagnostics:** error and warning structures
- **Strings:** length, comparison, concatenation, searching, and memory helpers

Additional API notes are available in the [`help/`](help/) directory.

## Examples and tests

Example and test sources are stored under [`example/`](example/) and [`test/`](test/).

```bash
gcc -std=c11 -Iinclude example/UnitTest.c -o UnitTestExample
```

The exact source and include requirements vary between standard-C and GNU-oriented variants, so compile the matching files together and use `-DOPENCF_FOR_GNU` consistently for GNU variants.

## Contributing

Contributions are welcome. When changing a public API:

1. Keep the standard-C and GNU-oriented naming consistent.
2. Add or update the relevant header documentation and help page.
3. Add focused coverage under `test/`.
4. Run examples and tests with both supported configurations where applicable.

## License

openCGL is licensed under the [GNU Lesser General Public License v2.1](LICENSE).