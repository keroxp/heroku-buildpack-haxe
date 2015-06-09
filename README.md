# heroku-builpack-haxe
haxe buildpack for heroku

## USAGE

- You need to create `build.hxml` file at your project root
- If you're using haxe in other framework, like Node.js, You need to set [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) as buildpacks. And create `.buildpacks` file at you project root.

```.buildpacks:txt
https://github.com/keroxp/heroku-buildpack-haxe
https://github.com/heroku/heroku-buildpack-nodejs
```

## Haxe and Neko VM options

You can specify your favorite version of haxe and NekoVM.
Createing `.haxerc` on you project root, this buildpack detect its content autmatically
and download specified binary of package. Example .haxerc file is as follows:

```.haxerc:sh
export HAXE_VERSION=3.1.3
export NEKO_VERSION=2.0.0
```

`.haxerc` file is just shell script that export snvironment variables and will be `source` in bin/compile.
If no version info are found, automatically downloded latest build version.
