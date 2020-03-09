Wabisabi is a completely modular operating system based on `wasi` and `wadi` specifications. It's usable by simply using a web component and declaring the kernel modules that should be used.

```html
<wabisabi-kernel>
    <kernel-module src="https://cdn.jsdelivr.net/gh/richardanaya/wabisabi/terminal.wasm"/>
    <kernel-module src="https://cdn.jsdelivr.net/gh/richardanaya/wabisabi/filesystem.wasm"/>
    <kernel-module src="https://cdn.jsdelivr.net/gh/richardanaya/wabisabi/framebuffer.wasm"/>
</wabisabi-kernel>
<script src="https://cdn.jsdelivr.net/gh/richardanaya/wabisabi/wabisabi.js"></script>
```

See it running [here](https://richardanaya.github.io/wabisabi/demo.html)

# Special Files

Wabisabi only has few special files to operate:

* `/kernel/run` - a file that can be written into to run a process
* `/kernel/load` - a file that can be written into to load a module
* `/kernel/modules/` - a directory that lists actively running modules

# Starting a process

Start a process by specifying the wasm binary to run with input and output file

```rust
libw::write_text("/kernel/run","1234->12314->13241")
```

# List active modules

Active modules just show up as their name under the modules folder

```rust
libw::list_files("/kernel/modules/")
```

# Load a module

Load a module by writing a url into the modules directory

```rust
libw::write_text("/kernel/modules/cowbell","https://cowbell.app/cowbell.wasm")
```

# Unoad a module

Unload a module by deleting it

```rust
libw::delete("/kernel/modules/cowbell")
```

# License

This project is licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or
   http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or
   http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in `libw` by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
