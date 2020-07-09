# Maintaining a custom Postgres install

## Compiling from source

While specific versions of postgres can be downloaded or installed from package managers like Homebrew, the extensions are usually only available prebuilt for the latest version.

Also, installing your dependencies via Homebrew will burn you since it will some day upgrade these to the latest version but leaving you without the older ones so you can't upgrade your database with it.

## PostGIS



### `configure: error: could not find libproj - you may need to specify the directory of a PROJ.4 installation using --with-projdir`

If you've compiled and installed the latest PROJ, `./configure` might still think it should use a proj install from Homebrew. Simply add `--with-projdir /usr/local` to the configure call.
