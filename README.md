# workflow-curl-view.and.data.api

Demonstrates the Autodesk View and Data API authorisation and translation process using cURL in command line scripts.


## Description

The workflow-curl-view.and.data.api sample exercises the curl commands demonstrating the Autodesk View and Data API authorisation and translation process mentioned in the Quick Start guide.

It closely follows the steps described in the documentation:
* http://developer.api.autodesk.com/documentation/v1/vs_quick_start.html

In order to make use of this sample, you need to register your consumer key, of course:
* https://developer.autodesk.com > My Apps

This provides the credentials to supply to the curl command script arguments.


## Motivation

What do you think about setting up a sample repository that does nothing but execute the sample shell scripts provided in the quick start documentation?

That would presumably help developers debugging their processes quickly. Probably everyone is copying and modifying those curl commands anyway. Here is therefore a set of Unix shell scripts. The Mac/Linux versions use BASH script/Python which are installed by default anyway.


## Dependencies

Standard OS functionality and cURL.

* http://en.wikipedia.org/wiki/CURL

This sample targets Unix only, it should run on different distribution of Linux and Mac OSX as well. For windows user, you need to install a unix shell like [cygwin](http://cygwin.com).

## Setup/Usage Instructions

  1. Make sure curl is installed in your system; if not, please refer to the
     [cURL releases and downloads](http://curl.haxx.se/download.html).
  2. Check that cURL is running in a Terminal window:<br />
     ```
     curl -V
     ```
  3. Request your consumer key/secret key from [https://developer.autodesk.com](https://developer.autodesk.com).
  4. Copy or rename the ./scripts/credentials_ file into ./scripts/credentials:<br />
     ```
     cp ./scripts/credentials_ ./scripts/credentials
     ```
  5. Copy your keys into the ./scripts/credentials file.
  6. Optionally, setup your WEB server - see instructions below in the 'Local WEB server' section.

The ./viewerAPI scripts provide quick help information for the commands and arguments.

A typical workflow is:

    # Do authentication
    ./viewerAPI auth

    # Create a bucket. Bucket name must be lower case and valid characters <br />
    ./viewerAPI bucketCreate my_bucket_name

    # Upload a model
    ./viewerAPI upload samples/Au.obj

    # Register the model to get it translated
    ./viewerAPI register Au.obj

    # Wait until the translation completes.
    # Translation is complete when it reaches 'success - 100%'
    ./viewerAPI registerProgress Au.obj

    # Retrieve preview image (png saved into ./temp/)
    ./viewerAPI thumbnail Au.obj

    # View the model in your localhost WEB site (html saved into ./temp/ and posted to your localhost)
    sudo ./viewerAPI html Au.obj

Note your access token and bucket name are saved in the data folder to be used as default by the scripts, but you can edit them as you wish.

Bucket information (JSON replies) returned by the system is stored in the data folder as well.


## Sample Log of Complete Process

Here is a copy of the log file from a successful real-world execution run on Mac OSX:

    ./viewerAPI auth
    ./viewerAPI bucketCreate my_bucket_name
    ./viewerAPI upload samples/Au.obj
    ./viewerAPI register Au.obj
    ./viewerAPI registerProgress Au.obj
    ./viewerAPI registerProgress Au.obj
    ./viewerAPI thumbnail Au.obj
    # start a local web server first, for Mac OSX Mountain Lion
    sudo apachectl start
    sudo ./viewerAPI html Au.obj


## Local WEB server

### Mac OSX

Starting Mountain Lion, there is an Apache WEB server pre-installed on Mac OS X, so there is no need to install it. However, you need to start the Apache WEB server, using a Terminal window.

1. Open the Terminal (it can be found under the Applications -> Utilities section).
2. Type the following command: <br />
   ```
   sudo apachectl start
   ```
   <br />This will start the Apache WEB server.
3. To make sure that it is working, open a browser and type `http://localhost` in the address bar.
   If you see a “It works!” message, then your Apache server is running fine.


### Linux

You need to install a WEB server, apache for instance, the way to install and run apache may be different according to the distribution you are using.


## License

workflow-curl-view.and.data.api is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT). Please see the [LICENSE](LICENSE) file for full details.


## Written by

Cyrille Fauvel, Autodesk Inc. <br />
Autodesk Developer Network <br />
http://www.autodesk.com/adn <br />
http://around-the-corner.typepad.com <br />
