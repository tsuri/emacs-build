# emacs-build

My scripts for building emacs and emacs-in-docker.

`./build DEBIAN_RELEASE EMACS_RELEASE`

if `DEBIAN_RELEASE` is `LOCAL`, build `EMACS_RELEASE` on host.  This
works if the host is running debian, otherwise you'll need to modify
the scrips, mainly `./scripts/install_dependencies`.  When building
locally, we assume having write access to `/usr/local`.  We keep
sources in `/usr/local/emacs_sources`, we build in
`/usr/local/emacs_build` and install the final emacs in
`/usr/local/emacs_dist`.

otherwise builds Emacs in a docker container using `EMACS_RELEASE` as
a base image. I think I used over time stretch, buster and bullseye,
but I haven't tried to keep the list of dependencies back compatible.

`EMACS_RELEASE` can be a released version, like 27.2.  Or a release
candidate like 27.2-rc1.  Or the special 'master' that downloads and
compiles the bleeding edge head of the master branch

`--with-native-compilation` is hardcoded for master.
If you want a non-native build of master you'll need to edit
the scripts.

The `run` scripts allow you to run the docker image with your home
directory mounted.  User ID and group ID there is hardcoded to
1000:1000, I should do a better job at it
