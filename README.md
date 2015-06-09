# heroku-builpack-haxe
haxe buildpack for heroku

## USAGE

- You need to create `build.hxml` file at your project root
- If you're using haxe in other framework, like Node.js, You need to set [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) as buildpacks. And create `.buildpacks` file at you project root.

```txt:.buildpacks
https://github.com/keroxp/heroku-buildpack-haxe
https://github.com/heroku/heroku-buildpack-nodejs
```

## Build Process

This buildpack will compile your haxe project by `haxe` command with `build.hxml` file.
By default, Haxe command line tools are not installed in Heroku Stack. So this buildpack will install all packages used to execute `haxe` and `haxelib` command, resolving dependencies and execute-path information. Packages to be downloaded are as follows:

- Compiled Haxe and Haxelib binary for 32/64bit Linux Machine
- Compiled Neko VM pakcage for 32/64bit Linux Machine
- libgc (and its dependencies)

After download, library files are expanded into $BUILD_DIR/lib, and executables into $BUILD_DIR/bin.

Finally, ensuring to use `haxe` and `haxelib` commands, it build your project based on `build.hxml` file.

## Grunt Compativility

If you're using **Grunt** to compile haxe files, pay special attention to your Grunt Tasks.
Probably tasks that includes grunt-contrib-haxe will not work because of not finding `haxe` command.
It will be caused by a lack of $PATH information. Currently I'm not sure how to path grunt PATH information,
tasks that using grunt-contirb-haxe will crash and build process fail although actually compilation of haxe have successed.

I reccomend you not to run grunt task for compiling haxe file, just to use this buildpack.

## Haxe and Neko VM options

You can specify your favorite version of haxe and NekoVM.
Createing `.haxerc` on you project root, this buildpack detect its content autmatically
and download specified binary of package. Example .haxerc file is as follows:

```sh:.haxerc
export HAXE_VERSION=3.1.3
export NEKO_VERSION=2.0.0
```

`.haxerc` file is just shell script that exports environment variables and will be `source` in build process.
If no version info are found, it automatically downlods latest build version.
