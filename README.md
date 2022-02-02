# SynShine distribution package

This document describes how to install and run the two components of SynShine:
The code correction server and VSCode plugin.

## Running the code correction server

We provide the code correction server as a Docker image hosted publicly on
DockerHub as `noahrose/synshine-server`. The image can be downloaded and run
with the following command:

```
docker run --rm -it -p 5000:5000 noahrose/synshine-server:latest
```

Or, run the provided shell script `start_correction_server.sh`.

The server will respond to HTTP requests on port 5000. Code correction requests
are handled via HTTP POST requests on the `/correct` endpoints. For example, the
following command will send the contents of `/path/to/code.java`.

```
curl --data-urlencode code@/path/to/code.java http://localhost:5000/correct
```

The response from the server will contain the corrected code.

## Using the VSCode extension

We provide an extension to the popular code editor "Visual Studio Code" for
interacting with the aforementioned code correction server.

The extension has been packaged as `synshine.vsix` and is included in this
distribution package. For instructions on how to install the extension, please
refer to
[this guide](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix)

Once the extension has been installed, and the code correction server is
running, open any java file in VSCode and a button will appear in the bottom
status bar titled "SynShine". Clicking on the button will initiate code
correction on the current file.
