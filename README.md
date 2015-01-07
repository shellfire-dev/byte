# `byte`: functions module for [shellfire]

This module provides an immature framework for manipulating byte and bit values from shell script.

## Overview

For example, to test if a bit is set:-

```bash
# tests if bit 1 (zero based) of value 3 is set
if byte_isBitSet 3 1; then
	echo "Success"
fi
```

## Importing

To import this module, add a git submodule to your repository. From the root of your git repository in the terminal, type:-
```bash
mkdir -p lib/shellfire
cd lib/shellfire
git submodule add "https://github.com/shellfire-dev/byte.git"
cd -
git submodule init --update
```

You may need to change the url `https://github.com/shellfire-dev/byte.git"` above if using a fork.

You will also need to add paths - include the module [paths.d].


## Namespace `byte`

### To use in code

If calling from another [shellfire] module, add to your shell code the line
```bash
core_usesIn byte
```
in the global scope (ie outside of any functions). A good convention is to put it above any function that depends on functions in this module. If using it directly in a program, put this line _inside_ the `_program()` function:-

```bash
_program()
{
	core_usesIn byte
	…
}
```

### Functions

***
#### `byte_isBitSet()`
|Parameter|Value|Optional|
|---------|-----|--------|
|`value`|Byte value as a number. Signed or unsigned irrelevant.|_No_|
|`bitIndex`|Zero based bit between 7 and 0 inclusive (not validated)|_No_|

Return code is zero if set, non-zero it otherwise.

***
#### `byte_printBinary()`
|Parameter|Value|Optional|
|---------|-----|--------|
|`value`|Byte value as a number. Signed or unsigned irrelevant.|_No_|

Writes eight binary digits of 0 or 1 to standard out.

***
#### `byte_setBit()`
|Parameter|Value|Optional|
|---------|-----|--------|
|`value`|Byte value as a number. Signed or unsigned irrelevant.|_No_|
|`bitIndex`|Zero based bit between 7 and 0 inclusive (not validated)|_No_|

Takes the value `value`, sets the bit `bitIndex` to 1 and writes the resultant value to standard out.





[swaddle]: https://github.com/raphaelcohn/swaddle "Swaddle homepage"
[shellfire]: https://github.com/shellfire-dev "shellfire homepage"
[core]: https://github.com/shellfire-dev/core "shellfire core module homepage"
[paths.d]: https://github.com/shellfire-dev/paths.d "paths.d shellfire module homepage"
