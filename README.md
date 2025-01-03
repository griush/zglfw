# zglfw
Zig GLFW bindings

## Usage
Run `zig fetch --save git+https://github.com/griush/zglfw`.

Add in `build.zig`:
```zig
const zglfw = b.dependency("zglfw", .{});
exe.root_module.addAnonymousImport("zglfw", .{
    .root_source_file = zglfw.path("glfw3.zig"),
    .target = target,
    .optimize = optimize,
});
```