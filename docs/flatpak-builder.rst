Flatpak Builder
===============

If an application requires additional dependencies that aren't provided by its runtime, Flatpak allows them to be bundled as part of the app itself. This requires building each module inside the application build directory, which can be a lot of work. The `flatpak-builder` tool can automate this multi-step build process.

flatpak-builder takes care of the routine commands used to build an app and any bundled libraries, thus allowing application building to be automated. To do this, it expects modules to be built in a standard manner by following what is called the [Build API](https://github.com/cgwalters/build-api). If any modules don't conform to this API, they will need to be modified.

Manifests
---------

The input to flatpak-builder is a json file that describes the parameters for building an app, as well as each of the modules to be bundled. This file is called the manifest. Module sources can be of several types, including .tar or .zip archives, Git or Bzr repositories, patch files or shell commands that are run.

The GNOME Dictionary manifest is short, because the only module is the application itself:::

      {
        "app-id": "org.gnome.Dictionary",
        "runtime": "org.gnome.Platform",
        "runtime-version": "3.22",
        "sdk": "org.gnome.Sdk",
        "command": "gnome-dictionary",
        "finish-args": [ 
           "--socket=x11", 
           "--share=network"  
        ],
        "modules": [
          {
            "name": "gnome-dictionary",
            "sources": [
              {
                "type": "archive",
                "url": "https://download.gnome.org/sources/gnome-dictionary/3.22/gnome-dictionary-3.22.0.tar.xz",
                "sha256": "efb36377d46eff9291d3b8fec37baab2355f9dc8bc7edb791b6a625574716121"
              }
            ]
          }
        ]
      }
