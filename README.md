# zglfw
Zig GLFW bindings

## Usage
Run `zig fetch --save git+https://github.com/griush/zglfw`.

Add in `build.zig`:
```zig
// module links libc
const zglfw = b.dependency("zglfw", .{});
module.addAnonymousImport("glfw", .{
    .root_source_file = zglfw.path("glfw3.zig"),
    .target = target,
    .optimize = optimize,
});

if (builtin.os.tag == .windows) {
    module.addLibraryPath(zglfw.path("bin/windows-mingw64/"));
    module.linkSystemLibrary("Gdi32");
}
module.linkSystemLibrary("glfw3");
```