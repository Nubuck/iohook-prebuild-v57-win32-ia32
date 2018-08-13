# iohook prebuild v57 win32 ia32

## About

This repo contains working [iohook](https://github.com/WilixLead/iohook) prebuilds for node 8.9.3 and electron 2.0.0 both ABI 57 for true win32 ia32 targets.

This repo is part of and investigation for an [issue over at the iohook repo](https://github.com/WilixLead/iohook/issues/70).

The prebuilds contained in this repo were build on the following platform:

 - A Windows 7 32bit, IE 11 [virtualBox](https://www.virtualbox.org/) downloaded from [Microsoft Virtual Machines](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/)
 - [Node v8.11.2 32bit](https://nodejs.org/download/release/v8.11.2/node-v8.11.2-x86.msi)
 - [Yarn](https://yarnpkg.com/en/docs/install#windows-stable)
 - [CMake](https://cmake.org/files/v3.12/cmake-3.12.1-win32-x86.msi)
 - [Windows Build Tools](https://yarnpkg.com/en/package/windows-build-tools)
 
Git was also installed from git bash capabilities, but probably not required.

Please note: [Windows Build Tools](https://yarnpkg.com/en/package/windows-build-tools) installs Python to the local user folder, but not 
necessarily the user nor environment PATH, and should be added manually.

## Build steps

Once the platform was setup, the [iohook](https://github.com/WilixLead/iohook) repo was cloned and the out of scope targets removed from the ```package.json``` file, shown below:

```json
{
  "supportedTargets": [
    [
      "electron",
      "2.0.0",
      "57"
    ],
    [
      "node",
      "8.9.3",
      "57"
    ]
  ]
}

```
 
Then running the deploy script handled the rest:

```
yarn run deploy

```

or 

```
node build.js

```

## Overwriting iohook ia32 prebuilds

Once the native addons are compiled into the ```builds``` folder, replace the iohook builds in your project.

For example the files located below in an electron project:

```
C:\apps\electron-app\node_modules\iohook\builds\electron-v57-win32-ia32\build\Release

```

This can be implemented an a post-build script in the project as a temporary work around until the  [issue over at the iohook repo](https://github.com/WilixLead/iohook/issues/70) is resolved. 