[![cUrl](https://img.shields.io/badge/cUrl-7.47.1-blue.svg)](https://nodejs.org/)
![Platforms](https://img.shields.io/badge/platform-windows%20%7C%20osx%20%7C%20linux-lightgray.svg)
[![License](http://img.shields.io/:license-mit-blue.svg)](http://opensource.org/licenses/MIT)

*Forge API*:
[![oAuth2](https://img.shields.io/badge/oAuth2-v1-green.svg)](http://autodesk-forge.github.io/)
[![Data-Management](https://img.shields.io/badge/Data%20Management-v1-green.svg)](http://autodesk-forge.github.io/)
[![OSS](https://img.shields.io/badge/OSS-v2-green.svg)](http://autodesk-forge.github.io/)
[![Model-Derivative](https://img.shields.io/badge/Model%20Derivative-v2-green.svg)](http://autodesk-forge.github.io/)
[![Viewer](https://img.shields.io/badge/Forge%20Viewer-v6.2-green.svg)](http://autodesk-forge.github.io/)


# forge.commandline-curl

<b>Note:</b> For using this sample, you need a valid oAuth credential.
Visit this [page](https://developer.autodesk.com) for instructions to get on-board.

Demonstrates the Autodesk Forge API authorisation and translation process using cURL
in command line scripts.


## Description

This sample exercises the cURL command demonstrating the Forge OAuth authorisation and
Model Derivatives API mentioned in the Quick Start guide.

In order to make use of this sample, you need to register your consumer key, of course:
* https://developer.autodesk.com > My Apps

This provides the credentials to supply while calling the Forge WEB service API endpoints.


## Dependencies

Standard OS functionality, Bash, cURL and JQ.

* http://en.wikipedia.org/wiki/CURL
* https://en.wikipedia.org/wiki/Bash_(Unix_shell)
* https://stedolan.github.io/jq/

This sample targets Mac OSX and Unix only, it should run on different distribution of Linux but was tested
on Ubuntu and Fedora only at this time.

Windows user, you need to install a Unix shell like [cygwin](http://cygwin.com) or [Git for Windows](https://git-scm.com/download/win),
but the sample requires bash 3.2 minimum to run. See the Windows special setup instructions for more details.


## Setup/Usage Instructions

Windows user, see  Windows special setup instructions below first.

  1. Make sure cURL is installed in your system; if not, please refer to the
     [cURL releases and downloads](http://curl.haxx.se/download.html).
  2. Check that cURL is running in a Terminal window:<br />
     ```
     curl -V
     ```
  3. Request your consumer key/secret key from [https://developer.autodesk.com](https://developer.autodesk.com).
  4. Set 2 environment variables FORGE_CLIENT_ID / FORGE_CLIENT_SECRET to hold your consumer key/secret keys.
  5. Install JQ
     ```
     brew install jq
     ```


The ./forge scripts provide quick help information for the commands and arguments.

A typical workflow is:

    # Do authentication
    ./forge 2legged

    # Create a bucket. Bucket name must be lower case and valid characters
    ./forge bucketCreate my_bucket_name

    # Upload a model
    ./forge upload samples/Au.obj

    # Translate the model
    ./forge translate Au.obj

    # Wait until the translation completes.
    # Translation is complete when it reaches 'success - 100%'
    ./forge translateProgress Au.obj

    # Retrieve preview image (png saved into ./temp/)
    ./forge thumbnail Au.obj

    # View the model in your localhost WEB site (html saved into ./temp/)
    ./forge html Au.obj

Note your access token and bucket name are saved in the data folder to be used as default by the scripts,
but you can edit them as you wish.

Bucket information (JSON replies) returned by the system is stored in the data folder as well.


### Windows special setup instructions

This sample was tested on Windows with the [git for windows](http://git-for-windows.github.io/) package.
It provides a nice terminal windows running Bash v4.3 and cUrl v7.51 already installed.

  1. Go to [http://git-for-windows.github.io/](http://git-for-windows.github.io/) and install the package.
     Select the default options.
  2. Go to [https://stedolan.github.io/jq/download/](https://stedolan.github.io/jq/download/), install JQ,
     and rename it to jq.
  3. Start the 'Git Bash' Terminal window from the Desktop icon, or a shortcut running this command
     ``` "C:\Program Files\Git\git-bash.exe" --cd-to-home ```
  4. Put the sample directory into the PATH.
  5. You can now continue with the normal setup instructions.


## License

This sample is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT).
Please see the [LICENSE](LICENSE) file for full details.


## Written by

Cyrille Fauvel <br />
Forge Partner Development <br />
http://developer.autodesk.com/ <br />
http://around-the-corner.typepad.com <br />
