# Sitevision Assets

## Project Structure
`public`
`dist`
`src`



    $ npm install

    $ bower update

    $ grunt watch
    $ grunt build
    $ grunt dist

    $ grunt build --sourcemaps


    $ grunt clean
    $ grunt clean:dist
    $ grunt clean:build



## Development Setup
Checkout the source code to your workspace:

    $ git clone git@github.com:malmostad/sitevision_assets.git

After cloning the repository, install the required Node.js dependencies for the project. Be sure to have [Node.js](http://nodejs.org) installed on your machine. Run:

    $ npm install

The dependencies defined in `package.json` will be installed in `node_modules`i the projects root. That directory is excluded in the `.gitignore` file from being committed with Git so you need to run the `npm install` command again if you switch to another local machine. To update the dependencies later, run `npm update`.


### Directory Structure



## Development

During development, you want the asset files to be re-compiled automatically when you make changes to the source code. Use the Grunt `watch` task available in the project:

    $ grunt watch

The Sass and CoffeeScript files in the `src` directory will be compiled to the `public` directory as soon as they are changed and at the startup of the `watch` task. The `public` directory is automatically cleaned when you run the task.


### Add Sass Files

### Add CoffeeScript Files


## Run a Local Asset Server
The easiest way to serve the assets on your own machine during development is to fire up a lightweight server and have the `watch` Grunt task running. The project is configured with two alternatives that works in the same way.

### Using Express
You have already Express installed if you ran `npm install` in the setup step above. To serve the assets locally on your machine with [Express](http://expressjs.com/), run:

    $ coffee app.coffee
    $ grunt watch

The assets are now available for your local web browser at e.g. `http://localhost:3000/application.css`. Express is reading static files from the `public` directory. Be sure to have the `watch` Grunt task running to have those files compiled whenever a source code file is changed.


### Using Sinatra
The project is also configured to use [Sinatra](http://www.sinatrarb.com/) to serve the assets locally during development. Be sure to have Ruby installed on your machine and run the following command on your machine to enable Sinatra:

    $ gem install sinatra

Start the local asset server:

    $ rackup
    $ grunt watch

The assets are now available in your local web browser at e.g. `http://localhost:9292/application.css`. Sinatra is reading static files from the `public` directory.  Be sure to have the `watch` Grunt task running to have those files compiled whenever a source code file is changed.

### Load in Tomcat
A third way to serve the assets locally is by using Sitevisions bundled Tomcat server if you have Sitevision running locally. Follow the instructions for deploying the assets as a servlet below, but perform it on your local machine. After the servlet is loaded once, you can symlink the servlet's directory to the `public` directory in your workspace.


## Build for Deployment
Do not use the files in the `public` directory when you deploy to a test or production server. To generate minified versions of the asset files, run:

    $ grunt dist

A new version will be compiled for deployment in the `dist` directory. The directory will be cleaned before the new files are generated.

To generate a Java servlet for deployment in the Tomcat server that Sitevision is running in, add the `--war` argument to the command:

    $ grunt dist --war

A Java servlet named `local-assets-v4` will be compiled to the `dist` directory.

## Deploy

The proven way is to deploy the assets as a servlet in Tomcat. Manually uploading in the CMS GUI is not recommended. In Sitevsion 3.x, servlets are deployed in `sitevision/tomcat/webapps`. Copy the war file to that directory and it will automatically be deployed if hot deployment is active.


## Update Shared Files

    $ bower update

### Release

    $ npm version patch
    $ npm version minor
    $ npm version major

    $ git push

    $ git tag
    $ git tag v4.0.1
    $ git push tags



## License
Released under AGPL version 3.
