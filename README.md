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
    exe.addLibraryPath(zglfw.path("bin/windows/"));
    exe.linkSystemLibrary("Gdi32");
}
exe.linkSystemLibrary("glfw3");
```