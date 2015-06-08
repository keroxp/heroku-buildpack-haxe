# heroku-builpack-haxe
---
haxe buildpack for heroku

## USAGE

- You need to create `build.hxml` file at your project root
- If you're using haxe in other framework, like Node.js, You need to set [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) as buildpacks. And create `.buildpacks` file at you project root.

```.buildpacks:txt
https://github.com/keroxp/heroku-buildpack-haxe
https://github.com/heroku/heroku-buildpack-nodejs
```