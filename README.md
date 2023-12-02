<div align="center" style="display:grid;place-items:center;">
<br>
<img src="logo.png" />

</div>

## About

Linc is a small library to create a simple web application with zig using MVC

### How to use it ?

- Create model

```bash
const User = struct {
    username: []u8
    password: []u8
}
```

- Create route

```bash
cont ctrl = @import("path_to_ctrl.zig");
const UserRoute = struct {
    r: router.Router,
}
pub fn routes(args: anytype) @TypeOf(args) {
    args[0].append(r.newRoute("/", ctrl.index(args)));
    return args;
}
```

- Create a controller specification methods
```bash
const view = @import("path_to_view.zig");
pub fn index(args) handler.HttpHandler {
//render the view
const bytes = "Hello world";
var response = args[2];
view.render(response, bytes);
return handler.HttpHandler;
}

```

- Create custom service
```bash
const User = @import("path_to_file.zig");
pub fn save(filename: []cont u8, T:User) !void {
//read file collection
//convert data in object
//add user
//stringify the object as json
//write data
}

```

- Use redirection
```bash
handler.redirectTo("urlvalue")
```

- Use file to read data
```bash
const files = @import("util/files.zig");
const content = files.read("path_to_file");
```

- Use file to write data
```bash
const files = @import("util/files.zig");
files.write("path_to_file", content);
```

- Start server

file:///E:/lang/zig/doc/std/src/std/http/Server.zig.html#L747


- Handle request

file:///E:/lang/zig/doc/std/src/std/http/Server.zig.html#L767
```bash
const config = @import("route/config.zig");
const user_route = @import("path_to_userroute.zig");
const router = @import("path_to_userroute.zig");
var rconfig = RouterConfig.init();
var bounded = std.BoundedArray(router.Router, 14);
var args = {.bounded, .req, .res};
// as number of routes in app
user_route.routes(args);
for(bounded) |r| {
	config.handleRequest(r, "urlvvalue", "domain");
}
```

