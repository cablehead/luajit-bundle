## luajit-bundle

This is an experiment at packaging the ability to compile luajit applications
to standalone system binaries. It's inspired by Luke Gorrie's
[Snabbswitch](https://github.com/SnabbCo/snabbswitch) project.

At the moment it supports compiling a single Lua script to a standalone binary,
and makes the binary argv, argc available to the Lua script as the standard Lua
arg global.

## Dependencies

```
  $ luarocks install stdlib lua-path
```

## Usage

foo.lua:

```lua
  for i, v in ipairs(arg) do
    print(i, v)
  end
```

```bash
  $ bin/luajit-bundle foo.lua -o ./foo
  ...
  $ ./foo bar 123
  1       bar
  2       123
```

## TODO

Compiling a single Lua file isn't particularly useful. This needs the ability
to describe all the Lua modules which should be linked with the binary.

It'd be great if this could just be installed with luarocks. I'm a complete Lua
newb though. Is it possible to distributed runnable commands with luarocks?
