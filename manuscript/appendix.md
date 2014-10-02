
{backmatter}

# Appendix A: Environment Setup Tutorials {#appendix-a}

This section is divided into 3 sections. The **Basic** section which provides the most basic ways of setting up your development environment for _Phaser_, the **Advanced** section which are for experienced developers who want a more comfortable environment at the price of complexity, and the **Cloud** section where we have tutorials on how to develop without requiring anything other than a browser and a stable internet connection.

## Basic Setup

Here's a basic step-by-step tutorial on preparing your system for the workshop:

1. Download the [basic game template](https://github.com/bryanbibat/html5shmup-template/archive/2.1-v3.zip) from Github and extract it into a folder.

    ![](images/extract_code.png)

2. Download either [version 2](http://www.sublimetext.com/2) or [beta version 3](http://www.sublimetext.com/3) of Sublime Text and install it in your computer.
3. In Sublime Text, add the folder you extracted to the current project by using `Project` -> `Add Folder to Project...`

    ![](images/sublime.png)

4. This last step, setting up a web server, will depend on your operating system:

    If you're using **Windows**, the smallest and easiest web server to setup is [Mongoose](http://cesanta.com/mongoose.shtml).

    If you're using a **Mac** or a **Linux** / **Unix** machine, the easiest is [Python](https://www.python.org/)'s `SimpleHTTPServer` since pretty much all of these OSs have Python pre-installed.

### Mongoose Setup

Repeating Mongoose's [tutorial](http://cesanta.com/docs/FileSharing.shtml): 

1. Download Mongoose Free Edition and copy it into the working folder.

    ![](images/mongoose.png)

2. Run Mongoose. Unblock the firewall for Mongoose by clicking `Allow access`.

    ![](images/mongoose_firewall.png)

3. Your browser should now be open at the game template.

    ![](images/mongoose_finished.png)

### Starting a Simple Python HTTP Server

1. Open your terminal and go to your working folder.
2. Run `python -m SimpleHTTPServer`.
3. Open your browser to [http://localhost:8000/](http://localhost:8000) to access your game.

    ![](images/python.png)
    
## Advanced Setup

Some experienced web developers might open the basic template and be disappointed at how plain it looks compared to the code they use in their day to day work. To answer this problem, I've made a couple of alternative templates that have the 2 features that I can't live without when developing front-ends: [LiveReload](http://livereload.com/) and a means for concatenating/minifying/preprocessing JS and CSS.

### JavaScript / NodeJS Template

You can find a starting template for NodeJS at the [`javascript` branch of the base template](https://github.com/bryanbibat/html5shmup-template/tree/javascript).

This template is a slightly modified version of Luke Wilde's [phaser-js-boilerplate](https://github.com/lukewilde/phaser-js-boilerplate) which uses Browserify, Jade, Stylus, Lodash, JsHint, Uglify.js, Google Analytics, Image optimisation tools, LiveReload, Zip compression, and partial cache busting for assets.

To setup:

{linenos=off,lang="text"}
~~~~~~~~
$ git clone https://github.com/bryanbibat/html5shmup-template.git
$ cd html5shmup-template
$ git checkout javascript
$ npm install
~~~~~~~~

Run [`grunt`](http://gruntjs.com/) (which you might have to install via `npm install -g grunt-cli`) to start server and open the default browser to [http://localhost:3017](http://localhost:3018). You can change the port settings in `src/js/game/properties.js`.

Run `grunt build` to compile everything (pre-process, concatenate, minify, etc.) to the `build` folder for production release.

Refer to the original boilerplate's Github Read Me for other details.

### Ruby Template

You can find a starting template for Ruby at the [`ruby` branch of the base template](https://github.com/bryanbibat/html5shmup-template/tree/ruby).

This template uses [Middleman](http://middlemanapp.com/) for features like LiveReload and Asset Pipeline. Compared to the NodeJS template, this template's set of libraries are more oriented towards the Ruby ecosystem: ERb and Haml instead of Jade, Sass instead of Stylus, and so on.

To setup:

{linenos=off,lang="text"}
~~~~~~~~
$ git clone https://github.com/bryanbibat/html5shmup-template.git
$ cd html5shmup-template
$ git checkout ruby
$ bundle install
~~~~~~~~

To start server:

{linenos=off,lang="text"}
~~~~~~~~
$ bundle exec middleman server
~~~~~~~~

Your game will be available at [http://localhost:4567](http://localhost:4567). Note that LiveReload is set up to work only for localhost, if you want to make it work on a different machine in the network, you must specify the host in `config.rb` e.g.

{linenos=off,lang="ruby"}
~~~~~~~~
 activate :livereload, host: 192.168.1.111
~~~~~~~~

To compile everything to the `build` folder:

{linenos=off,lang="text"}
~~~~~~~~
$ bundle exec middleman build
~~~~~~~~

Refer to the Middleman docs for other details.

Note that Middleman's Sprockets interface doesn't support audio so `audio_path` won't work. Check out `_preloader.js.erb` for my workaround.

## Cloud IDE Setup

Online IDEs like [Codio](https://codio.com/) and [Nitrous.IO](https://www.nitrous.io/) serve as alternative to desktop/laptop-based development. They take away the hassle of having to install additional software on your computer and replace it with the hassle of finding a venue that has reliable internet - this can be a big problem for workshops.

We'll run through the steps of setting up two types development environment: one using Codio on the basic template, and another using Nitrous.IO on the advanced Ruby template.

### Codio + Basic Template

1. Sign-up for Codio by filling out the form at [https://codio.com/p/signup](https://codio.com/p/signup).
2. At the dashboard, click "Create Project". Fill out the Project Name and choose Git with the Git repo being the template, [https://github.com/bryanbibat/html5shmup-template.git](https://github.com/bryanbibat/html5shmup-template.git), then click the "Create Project" button.

    ![](images/codio_create.png)

3. Wait until Codio finishes creating your project. You should be able to start editing your files once that is done.

    ![](images/codio_edit.png)

4. Click the "> Project Index (static)" button/link at the header to open your game in a new tab. You can also access your game by opening the URL shown in another browser tab or window.

    ![](images/codio_preview.png)

### Nitrous.IO + NodeJS Template

1. Sign-up for Nitrous.IO by filling out the form at [https://nitrous.io/users](https://nitrous.io/users).

2. At the dashboard, click "New Box". Choose the "Node.js" template, a Region close to you, and click the "Create Box" button. Leave the Github repository blank. 

    ![](images/nitrous_create.png)

3. Wait until Nitrous.IO finishes creating your project. Once that is done, checkout and setup the Ruby template with the same commands listed in the previous section:

    {linenos=off,lang="text"}
    ~~~~~~~~
    $ git clone https://github.com/bryanbibat/html5shmup-template.git
    $ cd html5shmup-template
    $ git checkout javascript
    $ npm install -g grunt-cli
    $ npm install
    ~~~~~~~~

    ![](images/nitrous_setup.png)

4. Open `src/js/game/properties.js`, modify the port to 3000, and run `grunt`:

    ![](images/nitrous_server.png)

5. Click the "Preview" -> "Port 3000" button/link at the header to open your game in a new browser tab.

    ![](images/nitrous_preview.png)

You can now edit your files and make your game. After saving, LiveReload will refresh the game automatically.

# Appendix B: Expected Code Per Chapter

We understand that there are cases you need to "cheat" and need to look for the "correct" code after each chapter. 

Maybe you've been spending too much time trying to find where you mistyped the code. Maybe a participant had to leave the workshop for 1 hour to deal with an emergency.

Regardless of the reason, here are the working code for each chapter of the workshop.

* **Overview of the Starting Code** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/d314e4e13d1d72cd11eefdd78d8b7f50ee9508c7), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/d314e4e13d1d72cd11eefdd78d8b7f50ee9508c7.zip)
* **Sprites, the Game Loop, and Basic Physics** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/820e4a7b34f17820d16d92ec085e07bf514b2646), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/820e4a7b34f17820d16d92ec085e07bf514b2646.zip)
* **Player Actions** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/57d5e0de70d28e0a75412b8db2dde42a27e250f6), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/57d5e0de70d28e0a75412b8db2dde42a27e250f6.zip)
* **Object Groups** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/edbbea67454be602f10d214f09175af4337d7b65), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/edbbea67454be602f10d214f09175af4337d7b65.zip)
* **Refactoring** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/29331d9d1f498bf3eb566b7b53c0b57db5c492d5), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/29331d9d1f498bf3eb566b7b53c0b57db5c492d5.zip)
* **Health, Score, and Win/Lose Conditions** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/54b3fef3486c94335a6f54092fdd60a22d4b6de0), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/54b3fef3486c94335a6f54092fdd60a22d4b6de0.zip)
* **Expanding the Game** 
  * **Harder Enemy** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/de293a2e5600fe9e31773cefb9a70fe2b666255c), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/de293a2e5600fe9e31773cefb9a70fe2b666255c.zip)
  * **Power-up** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/c27c08189f774d0035bf5b915af7bcdc4e013ee5), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/c27c08189f774d0035bf5b915af7bcdc4e013ee5.zip)
  * **Boss Battle** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/d42ded3af97490b8a514511f23122527f3aaceea), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/d42ded3af97490b8a514511f23122527f3aaceea.zip)
  * **Sound Effects** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/93478ee63d5761fd3e5e7b38cd172605442475c6), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/93478ee63d5761fd3e5e7b38cd172605442475c6.zip)
* **Wrapping Up**
  * **Restore original game flow** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/021431c4d4db7be736c83a4fe9c69c560e7e7bfd), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/021431c4d4db7be736c83a4fe9c69c560e7e7bfd.zip)
  * **Sharing your game** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/ccc532723237b733823fe8ec371f30415b3782c1), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/ccc532723237b733823fe8ec371f30415b3782c1.zip)

To make sure the lazy people don't cheat all the way, we won't provide links to solutions for the [_Challenges_](#challenges).
