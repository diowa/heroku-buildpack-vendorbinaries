# heroku-buildpack-vendorbinaries

Add support for vendor binaries during both compile and runtime.

This is a [Heroku buildpack](https://devcenter.heroku.com/articles/buildpacks)
for vendoring binaries into your project.

It is strongly inspired by [heroku-buildpack-apt](https://github.com/heroku/heroku-buildpack-apt) and [Heroku buildpack: Vendor Binaries](https://github.com/peterkeen/heroku-buildpack-vendorbinaries).

The problem with heroku-buildpack-apt is that sometimes libraries are old. If you
need a new version or a library that is not available as an apt package, then
this buildpack is for you.

## Usage

This buildpack is not meant to be used on its own, and instead should be in used
in combination with Heroku's [multiple buildpack support](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app).

Include a list of apt package names to be installed in a file named `Vendorfile`

## Example

This example will show how to provide GEOS and PROJ extensions to a Ruby based
application.

A repository using this approach is available at https://github.com/diowa/rgeo-sinatra

#### Command-line

To use the latest stable version:

```
heroku buildpacks:add --index 1 https://github.com/diowa/heroku-buildpack-vendorbinaries.git
```

#### Vendorfile

    # List urls
    https://vesuvius.herokuapp.com/libraries/geos-3.9.1-heroku.tar.gz
    https://vesuvius.herokuapp.com/libraries/proj-8.0.1-heroku.tar.gz

## Compile libraries for Heroku

If you are interested in compiling your own libraries, take a look at
[Vesuvius](https://github.com/tagliala/vesuvius)

## License

MIT
