# GitHub Format Experiment

> [!WARNING]
> This repository has been archived as I have found the answer to my questions.
> This is being kept for reference purposes.

I am curious how the "format" function works with more parameters than slots in
the template string.

## Summary

From a quick experiment, the result is that the `format` function can accept
any number of parameters that represent values to include in the format string
but it must include every value that the template references. This results in
it needing at least as many additional arguments as the maximum number argument
reference (plus one). For example: the call `format('{0}, {1}!', 'Hello')` will
fail as there is no argument corresponding to `{1}`.

However, this does not mean the `format` functions requires every single value
to be in the template string; values can be omitted from the template string
without issue. This is particularly useful if the template string comes from an
environment variable that only needs _some_ of the arguments. For example: the
call `format('{2}/{3}', 'White', 'Blue', 'Black', 'Red', 'Green')` will
successfully produce the string 'Black/Red'.
