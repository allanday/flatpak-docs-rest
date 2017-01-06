Building Simple Apps
====================

The `flatpak` utility provides a simple set of commands for building and distributing applications. These allow creating new Flatpaks, into which new or existing applications can be built. This section describes how to build a simple application which doesn't require any additional dependencies outside of the runtime it is built against.

Installing an SDK
-----------------

As described above, an SDK is a special type of runtime that is used to build applcations. Typically, an SDK is paired with a runtime that will be used by the app at runtime. For example the GNOME 3.22 SDK is used to build applications that use the GNOME 3.22 runtime. The rest of this guide uses this SDK and runtime for its examples. To do this, download the repository GPG key and then add the repository that contains the runtime and SDK:::
  
  $ flatpak remote-add --from gnome https://sdk.gnome.org/gnome.flatpakrepo
