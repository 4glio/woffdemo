[![Gitpod ready-to-code](https://img.shields.io/badge/Gitpod-ready--to--code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/4glio/woffdemo)

# WOFF Demo

This is a quick demo to showcase the "Binary Files" capability of the SASjs CLI.  This feature lets you compile arbitrary, binary content into SAS Web Services (Jobs on Viya, STPs on SAS 9 EBI, or Stored Programs on SASjs Server).

The compilation process (for Binary Files) works by converting the File into a Base64 encoded string and wrapping it in PUT statements.  A secondary step converts it back to binary, and makes it available in the user-provided fileref.

You can add Binary Files to your SASjs project by simply adding the parent folders in the `[binaryFolders](https://cli.sasjs.io/sasjsconfig.html#binaryFolders)` array of your `sasjsconfig.json` file (can be at both root and target level).

Once that's done, you include them in your SAS Jobs / Services / Tests by adding the following in your doxygen header:

```

  <h4> Binary Files </h4>
  @li mybinaryfile.png  myfilref
  @li anotherfile.xls myxlref

```

In this project we are compiling and deploying some WOFF files (fonts) for no other reason than we had a customer who was having CORS troubles and this approach was a neat workaround that didn't involve server configuration changes.

## Project Setup

First, install the SASjs CLI - `npm i -g @sasjs/cli`.

Next, authenticate to your target - eg `sasjs auth -t viya`

Finally, compile / build / deploy:  `sasjs cbd`

The services in the `sasjs/services/woffwoff` folder have been compiled and deployed to SAS.

## Authentication
To connect to viya you need a client & secret (configured with the authorization_code scope) from your administrator.  For more info, see [here](https://cli.sasjs.io/faq/#how-can-i-obtain-a-viya-client-and-secret).

Once you have these, run `sasjs auth -t YOURTARGET` to authenticate against the target you configured in the sasjs/sasjsconfig.json file.

## Compile, Build & deploy
The project contains a number of Services (see the `sasjs/sasjsconfig.json` file for locations of these).  To compile these jobs into a single build pack, and deploy to your appLoc (SAS Drive location) you can run the following command:

```
sasjs cbd -t viya
```

## Docs

To produce full HTML documentation of all the Jobs, Services, Macros and Programs you can run the command below.  This requires a local installation of *doxygen*.

```
sasjs doc
```

If you have questions or would like support, feel free to write the SASjs team an [issue](https://github.com/sasjs) on the relevant repository.


