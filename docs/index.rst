Welcome to Flatpak's documentation!
===================================

This covers everything you need to know to build and distribute applications as Flatpaks. The docs start with introduction to the basic concepts and a simple app building tutorial, before moving on to cover automated building and repository hosting.

Example tutorials are used throughout. To complete them, it is necessary to have flatpak and flatpak-builder installed on your system. [flatpak.org](http://flatpak.org/getting.html) has details on how to do this.

Key Concepts
------------

Flatpak is best understood through its key concepts: runtimes, bundled libraries, SDKs and sandboxes. These help to explain how Flatpak differs from traditional application distribution on Linux, as well as the framework's capabilities.

Runtimes
--------

Runtimes provide the environment that each application runs in, including the basic dependencies they might require. Each runtime can be thought of as a `/usr` filesystem (indeed, when an app is run, its runtime is mounted at `/usr`). Various runtimes are available, from more minimal (but more stable) Freedesktop runtimes, to larger runtimes produced by desktops like GNOME or KDE. (The [runtimes page](runtimes.html) provides an overview of the runtimes that are currently available.)

Each application must be built against a runtime, and this runtime must be installed on a host system in order for the application to run. Users can install multiple different runtimes at the same time, including different versions of the same runtime.

Flatpak identifies runtimes (as well as SDKs and applications) by a triple of name/arch/branch. The name is expected to be in inverse-dns notation, which needs to match the D-Bus name used for the application. For example: `org.gnome.Sdk/x86_64/3.14` or `org.gnome.Builder/i386/master`.

Bundled Libraries
-----------------

If an application requires any dependencies that aren't in its runtime, they can be bundled along with the application itself. This allows apps to use dependencies that aren't available in a distribution, or to use a different version of a dependency from the one that's installed on the host.

Both runtimes and app bundles can be installed per-user and system-wide.

Contents:

.. toctree::
   :maxdepth: 2

   getting-started
   building-simple-apps
   flatpak-builder
   hosting-a-repository
