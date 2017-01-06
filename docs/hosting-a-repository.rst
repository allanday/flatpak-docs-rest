Hosting a repository
====================

While it is relatively simple to host a flatpak repository, there are some important details to be aware of.

archive-z2 repositories contain a single file for each file in the application. This means that pull operations will do a lot of HTTP requests. Since new requests are slow, it is important to enable HTTP keep-alive on the web server.

OSTree supports something called static deltas. These are single files in the repo that contains all the data needed to go between two revisions (or from nothing to a revision). Creating such deltas will take up more space on the server, but will make downloads much faster. This can be done with ``build-update-repo --generate-static-deltas``.

GPG signatures
--------------

By default OSTree refuses to pull from a remote repository that is not signed. To disable GPG verification, the ``--no-gpg-verify`` option needs to be used when a remote is added. Alternatively, it can be disabled on an existing remote using flatpak remote-modify.

Note that gpg signatures are required for the user to be able to install trusted remotes that can be updated from without needing to be root.

OSTree requires signatures for every commit and on repository summary files. These objects are created by the ``build-update-repo`` and ``build-export`` commands, as well as indirectly by flatpak-builder. A GPG key should therefore be passed to each of these commands, and optionally the gpg home directory to use. For example:

Referring to repositories
-------------------------

A convenient way to point users to the repository containing your application is to provide a ``.flatpakrepo`` file that they can download and install. To install a ``.flatpakrepo`` file manually, use the command.
