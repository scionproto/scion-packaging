# SCION Utils

This repo contains the control files to create a `scion-utils` debian package. This includes:

-   scmp
-   showpaths
-   logdog
-   pingpong

## Build the package

Build the tools in the scion repo. E.g. `make` in `~/go/src/github.com/scionproto/scion`. Then copy
to binaries to `usr/bin`.

-   `cp ~/go/src/github.com/scionproto/scion/bin/scmp scion-utils/usr/bin/`
-   `cp ~/go/src/github.com/scionproto/scion/bin/showpaths scion-utils/usr/bin/`
-   `cp ~/go/src/github.com/scionproto/scion/bin/logdog scion-utils/usr/bin/`
-   `cp ~/go/src/github.com/scionproto/scion/bin/pingpong scion-utils/usr/bin/`

Update the changelog and gzip it: 
`gzip --best --keep scion-utils/usr/share/doc/scion-utils/changelog`

Then build the package with `fakeroot dpkg-deb --build scion-utils`. Rename it according its
version, e.g.: `mv scion-utils.deb scion-utils_0.1-1.deb`

## Deploy
Copy the package to `apt.scionproto.net` and follow the README.
