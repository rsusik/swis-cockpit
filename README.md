# SWIS wrapper for Cockpit

It is a [SWIS](https://github.com/rsusik/simple-web-based-interface-for-scanner) wrapper for Cockpit. 

It allows access to Scaner (SWIS) from Cockpit menu.

# Requirements

* SWIS service installed

# Important!

This project is in the development stage and, thus, is not ready to use out-of-the-box.

To use this project you have to:

1) manually edit `manifest.json` and replace all `http://192.168.1.105:5520` to a propoer ones (address and port of SWIS). Note: It will work only on `http` protocol so cockpit should be running on `http` as well (i.e. http://localhost:9090).
2) build the project (run `make`)
3) install the app in cockpit

# Screenshot

<img src="https://github.com/rsusik/swis-cockpit/raw/main/screenshot-01.png" width="300">

# Development dependencies

On Debian/Ubuntu:

    $ sudo apt install gettext nodejs npm make

On Fedora:

    $ sudo dnf install gettext nodejs npm make


# Getting and building the source

These commands check out the source and build it into the `dist/` directory:

```
git clone https://github.com/rsusik/swis-wrapper
cd swis-wrapper
make
```

# Installing

`make install` compiles and installs the package in `/usr/local/share/cockpit/`. The
convenience targets `srpm` and `rpm` build the source and binary rpms,
respectively. Both of these make use of the `dist` target, which is used
to generate the distribution tarball. In `production` mode, source files are
automatically minified and compressed. Set `NODE_ENV=production` if you want to
duplicate this behavior.

For development, you usually want to run your module straight out of the git
tree. To do that, run `make devel-install`, which links your checkout to the
location were cockpit-bridge looks for packages. If you prefer to do
this manually:

```
mkdir -p ~/.local/share/cockpit
ln -s `pwd`/dist ~/.local/share/cockpit/swis-wrapper
```

After changing the code and running `make` again, reload the Cockpit page in
your browser.

For more information see: https://cockpit-project.org/documentation.html
