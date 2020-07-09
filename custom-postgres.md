# Maintaining a custom Postgres install

## Compiling from source

While specific versions of postgres can be downloaded or installed from package managers like Homebrew, the extensions are usually only available prebuilt for the latest version.

Also, installing your dependencies via Homebrew will burn you since it will some day upgrade these to the latest version but leaving you without the older ones so you can't upgrade your database with it.

## PostGIS



### `configure: error: could not find libproj - you may need to specify the directory of a PROJ.4 installation using --with-projdir`

If you've compiled and installed the latest PROJ, `./configure` might still think it should use a proj install from Homebrew. Simply add `--with-projdir /usr/local` to the configure call.

### when linking: `Undefined symbols for architecture x86_64` for a bunch of json functions

If `make` gets to the linking stage and throws an error like this:

```
Undefined symbols for architecture x86_64:
  "_json_object_array_get_idx", referenced from
[...]
```

The included json lib might be too old. In my case, I could solve the problem similarly to the one with libproj:

`--with-jsondir /usr/local`

### `Library not loaded: /usr/local/opt/protobuf/lib/libprotobuf.21.dylib`

`--without-protobuf`
