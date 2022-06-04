# Classic openrouteservice maps client

[![Build Status](https://travis-ci.org/GIScience/openrouteservice-app.svg?branch=development)](https://travis-ci.org/GIScience/openrouteservice-app)

The classic openrouteservice(ors) maps client is an online route planning application that is based on open source software, open data and open standards.

It uses the [openrouteservice API](https://openrouteservice.org/) and needs a valid API key
(free up to a [certain request limit per day](https://openrouteservice.org/plans/))

![preview](https://cloud.githubusercontent.com/assets/10322094/26202903/63ccd808-3bd9-11e7-9a89-f06ad50d583e.png)

## Installation

Requirements:
- [git](https://git-scm.com/downloads)
- docker
- docker-compose

Clone the repository
```sh
git clone https://github.com/GIScience/openrouteservice-app.git

# switch to repository folder
cd openrouteservice-app
```

First Replace weathercheck.txt content with your Api-Key:
```sh
# Open `app/weathercheck.txt` in your favorite text editor and replace the content with your Token.
# e.g.:
vim app/weathercheck.txt
```

Build the docker image:
```
docker-compose build
```
## Running the client

Run docker-compose up:
```
docker-compose up -d
```

The app will be exposed on http://localhost:8035

## Running in development mode
- open on http://localhost:3005
- container will be removed after stopping

Normal endpoints:
```
docker-compose run -p 3005:3005 --rm ors-classic-maps dev
```

If you want to use the openrouteservice client with a
[local backend version of openrouteservice](https://github.com/GIScience/openrouteservice) make sure
you are using the correct *endpoint paths* in `ngconstant.local` of the `Grunfile.sample.js`.

Local ors backend:
```
docker-compose run -p 3005:3005 --rm ors-classic-maps ors_local
```

> Note: In case of CORS issues try setting the endpoints of the backend services to `http://localhost:3005`
> which should be proxied to `http://localhost:8082` by the `connect:dev` grunt task.

## Install dependencies locally

If you want to have all dependencies locally, installation is a bit more difficult.
Also, the commands for running the client are a bit different.

Requirements:

- [git](https://git-scm.com/downloads)
- [nodejs](https://nodejs.org/en/download/package-manager/)
- [Api-key](https://openrouteservice.org/sign-up/)

### Permission Issues
If you encounter any [permission issues](https://github.com/npm/npm/issues/18380) during the installation:

- *on Linux:* try running npm-commands with `sudo` :

e.g.:
```sh
sudo npm install
```
- *on Windows([GitBash](https://gitforwindows.org/) recommended):* try running npm-commands with the `--no-optional` flag:

e.g.:
```sh
npm install --no-optional
```

### Installation

After cloning the repository:

- Install dependencies:
```sh
# install all modules listed as dependencies in package.json
npm install
```

- Initiate default files:
```sh
# Copy `Gruntfile.default.js` to `Gruntfile.js`
cp Gruntfile.default.js Gruntfile.js

# Copy `weathercheck.default.txt` to `weathercheck.txt`
cp app/weathercheck.default.txt app/weathercheck.txt
```

Don't forget to edit `weathercheck.txt` and insert your API key.

### Run openrouteservice:

To enable console output information and logging for bug-fixing and feature development do:

	grunt dev

To build for production (all output in `build` folder):

	grunt ors

To use a local ors backend:

	grunt ors_local

## Contribution

If you would like to contribute, please note that we are using a [branching model](http://nvie.com/posts/a-successful-git-branching-model/) to structure our git workflow and are following [commit message guidelines](https://api.coala.io/en/latest/Developers/Writing_Good_Commits.html).

For minor bugfixes use the development branch:

	git checkout development

For new features, please create a new branch:

	git checkout -b feature_branch

Do a [pull request](https://help.github.com/articles/creating-a-pull-request/) to our development branch.
Be sure to pull the latest changes beforehand and fix any emerging conflicts.

## Translations

Help us to provide the openrouteservice in your language by translating some simple keywords!

In this [spreadsheet](https://docs.google.com/spreadsheets/d/1GzFPlVrqJBmUatfWft7v-vS_tfENGtAy0RHOv_5n3SU/edit#gid=0) you can add a column for your language or check the already added words if they are correctly translated. Our service will be updated regularly with the latest language versions.

If there are further questions, please let us know!

## License

(The MIT License)

Copyright (c) 2017 GIScience Research Group, Heidelberg University.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
