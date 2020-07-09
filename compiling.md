# Troubleshooting compiling from source

Contains troubleshooting advice when dealing with compiling from source.

This list will be updated every time I stumble upon something.

## Remember to install developer tools in XCode

`xcode-select --install`

This might also be needed after an XCode Software update.

## stdio.h not found

`CPPFLAGS="-isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.15.sdk" ./configure`

This sets the -isysroot of gcc to the correct one for your macOS version. Especially when compiling older software releases, the configure script will apparently fall back to 10.14 which does not exist on later systems. 

Maybe replace `MacOSX10.15.sdk` with something current.
