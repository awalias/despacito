# Despacito

[![stable](http://badges.github.io/stability-badges/dist/stable.svg)](http://github.com/badges/stability-badges)

Creates a new GitHub repository from your current folder, and then runs the initial `git` commands to commit and push the contents. If the folder has a `package.json` it will pull the repo's `description`, `name` and `homepage` from that. 

This repo was originally forked from the amazing [ghrepo](https://github.com/mattdesl/ghrepo) tool by Matt DesLauriers. 

It has since been rewritten from scratch and relicensed under the [Blue Oak Council License 1.0.0](https://blueoakcouncil.org/license/1.0.0).

Install:

```sh
npm install despo -g
```

The example below pushes the contents of `my-module` to a new GitHub repository with the specified commit message. On first run, it will [prompt for authentication](https://github.com/rvagg/ghauth).

```sh
#make a new module
mkdir my-module
cd my-module
npm init

#create a new GitHub repository
despo -m 'first commit yolo'
```

This should open the browser to the newly created GitHub repository on your account, and push the current contents of the folder.

![result](http://i.imgur.com/5bz7JCW.png)

## Usage

[![NPM](https://nodei.co/npm/despacito.png)](https://www.npmjs.com/package/despacito)

```
Usage:
  despo [opts]

Options:
  --help              show help
  --version, -v       prints version number
  --name, -n          the name of the repository
  --description, -d   the description
  --homepage, -h      the homepage URL
  --private, -p       mark the repository as private (default false)
  --message, -m       the commit message (default "first commit")
  --bare, -b          do not run any git commands after creating the repo
  --no-open           do not open the GitHub repo in the browser after creation
  --org, -o           the organization to create the repo in (optional)
```

The `--name`, `--description`, and `--homepage` will default to `package.json`. If no `package.json` is found, `--name` defaults to the current folder's name.

The `--org` will default to the same user as specified in the `repository` URL in package.json. Otherwise, it will default to the username specified from the initial authentication.

#### Default Commit Message

You can personalize the default commit message with npm config:

```sh
npm config set init.despo.message 'YOLO!'
```

Now `--message` will default to `'YOLO!'`.

## License

MIT, see [LICENSE.md](http://github.com/bookiza/despacito/blob/master/LICENSE.md) for details.
