# StackEdit-Electron

StackEdit on Electron.

![Screenshot](https://raw.githubusercontent.com/ajf-/MarkdownEditor/master/screenshot.png)

StackEdit-Electron is an [Electron](http://electron.atom.io) package for [StackEdit](https://stackedit.io/).

It is built out of the [Electron Quick Start](https://github.com/atom/electron-quick-start) repository and uses the [StackEdit](https://stackedit.io/) editor, which has a bunch of awesome features.

To run: 

```
npm install && npm start
```

To package: 

```
npm run package
``` 
**Note:** The package script is specific to my environment. Tweak if necessary.

## Development notes

StackEdit doesn't seem to be an "out of the box" solution, since it looks like it's mostly intended to be compiled and run directly, making a local server and using it's own database. It could be better to integrate Electron into StackEdit that the other way around. 

Some problems with this involve serving the resources, which have to be done in a special way (with an iframe for the frontend and disabling cluster support for the StackEdit server. 

Making the electron app start the server by including StackEdit's server seems like enough. I only had to a couple workarounds, which I did to keep things simple, but at the moment I am not entirely sure why they are needed. 

1. The StackEdit server needs to be fired up with clusters disabled. 
2. The main html page of Electron needs an iframe that serves StackEdit on localhost. 

## What works and what doesn't (as far as I know)

1. The top formatting bar works perfectly out of the box. 
2. I have not yet tested the cloud synchronizations, but I am guessing that serving from localhost will have some issues.
3. Save to disk works out of the box. 

## To do

- Probably investigate a way to use this in a more Electron-like way (without an express server in between). Currently I'm more concerned with using StackEdit as it is and trying not to do any modifications on it. 
- Testing the other various features of StackEdit. 
- Making StackEdit work out of a `file://` protocol instead of through the localhost server. 
- Add keyboard integration (`Cmd+C`, `Cmd+X`, `Cmd+S`, etc.).
- Make common StackEdit actions accessible on the toolbar.

## Help? 

Will you help me? Just send a pull request. 