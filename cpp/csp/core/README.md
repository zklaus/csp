The core library can be built with meson by following the steps given below,

1. `meson setup builddir`
2. `cd builddir`
3. `meson compile`

Note that you need to switch your working directory to `cpp/csp/core` from project root.

Workarounds that are yet to be reverted,

1. Change, `"` in includes to `<` and `>`.
2. Rename `Time1.h` to `Time.h`.
