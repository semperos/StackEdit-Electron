# MarkdownEditor

StackEdit on Electron.

![Screenshot](https://raw.githubusercontent.com/ajf-/MarkdownEditor/master/screenshot.png)

MarkdownEditor is a plain simple live markdown editor that is intended to help me write my posts and the documentation for my projects.

It's a fork of the [Electron Quick Start](https://github.com/atom/electron-quick-start) and uses the [StackEdit](https://stackedit.io/) editor, which has a bunch of awesome features.

To build and run: 

```
npm install && npm start
```


## Development notes

StackEdit doesn't seem to be an "out of the box" solution, since it looks like it's mostly intended to be compiled and run directly, making a local server and using it's own database. It could be better to integrate Electron into StackEdit that the other way around. 

Some problems with this involve serving the resources, which have to be done in a special way (with an iframe for the frontend and disabling cluster support for the StackEdit server. 

Making the electron app start the server by including StackEdit's server seems like enough. I only had to a couple workarounds, which I did to keep things simple, but at the moment I am not entirely sure why they are needed. 

1. The StackEdit server needs to be fired up with clusters disabled. 
2. The main html page of Electron needs an iframe that serves StackEdit on localhost. 

**Notes** 

1. The top formatting bar works perfectly out of the box. 
2. I have not yet tested the cloud synchronizations, but I am guessing that serving from localhost will have some issues.
3. Save to disk works out of the box. 

## Build

To build the packaged app, run:
````
npm run build
````
Note that the configuration of the `build` script in `package.json` is specific to my environment, so you might need to tweak it. 

## To do


- Probably investigate a way to use this in a more Electron-like way (without an express server in between). Currently I'm more concerned with using StackEdit as it is and trying not to do any modifications on it. 

