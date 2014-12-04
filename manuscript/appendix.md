
{backmatter}

# Appendix A: Environment Setup Tutorials {#appendix-a}

This section is divided into 3 sections. The **Basic** section which provides the most basic ways of setting up your development environment for _Phaser_, the **Advanced** section which are for experienced developers who want a more comfortable environment at the price of complexity, and the **Cloud** section where we have tutorials on how to develop without requiring anything other than a browser and a stable internet connection.

## Basic Setup

Here's a basic step-by-step tutorial on preparing your system for the workshop:

1. Download the [basic game template](https://github.com/bryanbibat/html5shmup-template/archive/2.2-v1.zip) from Github and extract it into a folder.

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

* **Overview of the Starting Code** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/ee644dba40a5061c49d117998bd499dd92a04bfd), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/ee644dba40a5061c49d117998bd499dd92a04bfd.zip)
* **Sprites, the Game Loop, and Basic Physics** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/344ac32dcffa76d14aa59a7b9eca01021cb61675), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/344ac32dcffa76d14aa59a7b9eca01021cb61675.zip)
* **Player Actions** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/3aa418ef34bf4a5c56056b9b4969f0f1cce33ac4), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/3aa418ef34bf4a5c56056b9b4969f0f1cce33ac4.zip)
* **Object Groups** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/debcac3d763c8bc00666c1aded907a61f8945501), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/debcac3d763c8bc00666c1aded907a61f8945501.zip)
* **Refactoring** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/477aa0b65f1450d12a411543993e0278217413b5), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/477aa0b65f1450d12a411543993e0278217413b5.zip)
* **Health, Score, and Win/Lose Conditions** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/b2ec5ef1d0cfb366b3df15145661dc3ed8d6644e), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/b2ec5ef1d0cfb366b3df15145661dc3ed8d6644e.zip)
* **Expanding the Game** 
  * **Harder Enemy** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/60e13aca737604822e524a6b5d4a2fffb8b54de6), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/60e13aca737604822e524a6b5d4a2fffb8b54de6.zip)
  * **Power-up** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/18c536a16a0a27829c59403d187bc83f55224bb2), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/18c536a16a0a27829c59403d187bc83f55224bb2.zip)
  * **Boss Battle** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/d68b99420b8f76c592278e66df1ebf6600c77bff), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/d68b99420b8f76c592278e66df1ebf6600c77bff.zip)
  * **Sound Effects** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/37cd365574cf5f27bbcb0ab104dba9394bd411f6), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/37cd365574cf5f27bbcb0ab104dba9394bd411f6.zip)
* **Wrapping Up**
  * **Restore original game flow** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/aa92aba3b0c1a2466093887a01566288fa1ca88f), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/aa92aba3b0c1a2466093887a01566288fa1ca88f.zip)
  * **Sharing your game** - [Browse in Github](https://github.com/bryanbibat/html5shmup-template/tree/347a18e60766b2c1fc68911aa98faaefa762ffa6), [Download Zip](https://github.com/bryanbibat/html5shmup-template/archive/347a18e60766b2c1fc68911aa98faaefa762ffa6.zip)

To make sure the lazy people don't cheat all the way, we won't provide links to solutions for the [_Challenges_](#challenges).
