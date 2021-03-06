# Configure `grunt-build-control`
For the most part, we will configure `grunt-build-control` just like we did for our webapp experiments. We will still be deploying our AngularJS sites to Github Pages because although we are creating much more complex Javascript applications, we are still only building a static website that requires no dynamic server to deliver. This is another of the amazing things about working with Javascript webapps.

# Install `grunt-build-control`
The `grunt-build-control` component must be installed into each project where you want to use it. Install it as usual and don't forget to add the `--save-dev` flag so your project remembers that you are using `grunt-build-control`. Run this command to install `grunt-build-control`:

```bash
npm install grunt-build-control --save-dev
```

## Let Grunt know that `grunt-build-control` is available
The `generator-angular` template uses `jit-grunt` to manage dependencies for your Grunt tasks. In this case, look for the definition that resembles this code:

```js
// Automatically load required Grunt tasks
require('jit-grunt')(grunt, {
    useminPrepare: 'grunt-usemin',
    ngtemplates: 'grunt-angular-templates',
    cdnify: 'grunt-google-cdn'
});
```

Modify that `require()` definition to add a `buildcontrol` line, like this:

```js
// Automatically load required Grunt tasks
require('jit-grunt')(grunt, {
    useminPrepare: 'grunt-usemin',
    ngtemplates: 'grunt-angular-templates',
    cdnify: 'grunt-google-cdn',
    buildcontrol: 'grunt-build-control'
});
```

## Configure the `buildcontrol` task
You also need to create the task object inside of `grunt.initConfig()`. To keep things easy, I advocate placing this definition right before the definition for the `watch` task (which is what Grunt uses to know when you've changed files when you are running the local server).

This should looks something like this:

```js
  // Define the configuration for all the tasks
  grunt.initConfig({

    // Project settings
    yeoman: appConfig,

    buildcontrol: {
      options: {
        dir: 'dist',
        commit: true,
        push: true,
        message: 'Built %sourceName% from commit %sourceCommit% on branch %sourceBranch%'
      },
      pages: {
        options: {
          remote: 'git@github.com:your_github_user/your_webapp.git',
          branch: 'gh-pages'
        }
      }
    },

    // Watches files for changes and runs tasks based on the changed files
    watch: {
    
    ... more code ...
```

Once you've completed these steps you may commit your code and deploy it.

## Commit and deploy
Commit your code using the same process you have before. Once you commit you should run:

`grunt build`

and then

`grunt buildcontrol`

Once the `buildcontrol` command completes, you can visit your project on Github Pages to see the files deployed. You should see the same thing you saw in your local development browser, and your addition calculator (if you went that far) should be fully functional.