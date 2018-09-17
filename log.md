# 100 Days Of Code - Log


## 20180917 - Day 3: Joker Clojure linter and SVG status bars


### Thoughts for today

I had a little excursion into [Joker](https://github.com/candid82/joker), a linter for Clojure.  Someone was having problems getting the [clojure-lint](https://github.com/n2o/clojure-lint-spacemacs-layer) layer to work in Spacemacs, so I though I would give it a try and see if I could help.  I really like the feedback I get from the Joker linter, its very clearly presented and is very fast.

I like coding interfaces with Scalable Vector Graphics (SVG) as the graphics are defined as data structures (when using the hiccup syntax).  So SVG is really easy to use with Clojure.  It requires a little trial and error as its not specifically documented as far as I can tell, but having a repl means is really quick to experiment.

### Code from today

Defined a status bar component using Hiccup syntax to generate SVG
* https://github.com/jr0cket/webapp-status-monitor/commit/4d7925184c8cf181f0addfb8fb829844ba56002d
* https://github.com/jr0cket/webapp-status-monitor/commit/17efddc7233fb134b107c89f88fe3875ff40f83c


### Activities in detail

#### Continuing the status-monitor webapp

I added some mock status bars to my status-monitor application, using hiccup and [Scalable Vector Graphics (SVG)](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics) to add some colour and design to the page.

There is a bit of a challenge with using SVG with the Hiccup syntax, as it does not seem to be documented anywhere.  However, its not that hard to work out by looking at the [SVG elements in HTML](https://developer.mozilla.org/en-US/docs/Web/SVG/Element).  We are generating HTML after all.

> I did find some SVG projects that may be interesting to try:
> [Tikkba](https://github.com/pallix/tikkba) for the creation and the dynamic modification of SVG documents
> [analemma](http://liebke.github.io/analemma/) for generating charts and Scalable Vector Graphics (SVG)
> [dali](https://github.com/stathissideris/dali) for representing the SVG graphics format. It allows the creation and manipulation of SVG files. The syntax used to describe the graphical elements is based on hiccup with a few extensions
> [svg-wrangler](https://github.com/gfredericks/svg-wrangler) a collection of Clojure functions to help assemble SVG images via hiccup data structures


#### Joker linter and clojure-lint layer in Spacemacs

I setup on [Joker](https://github.com/candid82/joker) on ubuntu by downloading a [pre-compiled linux binary](https://github.com/candid82/joker/releases) and placing it in `~/bin` which is already on my executable path.

Added the `clojure-lint` layer to `.spacemacs` configuration file and restarted Spacemacs with `SPC q r`.

Opened my status-monitor `status-monitor.handler` namespace and it showed me where I had been less clear with my code straight away.

If I call a function with the wrong number of argument then Joker will put an orange dot in the margin.  That's so awesome.

I will refactor a few things that Joker found tomorrow, such especially refining the namespace refer.

------------------------------------------

## 20180916 - Day 2: Investigating compojure-template and lein-ring

Today was more a journey of discovery on how projects from the compojure-template can be run and how the lein-ring plugin works.

### Thoughts for today

I really appreciated the work done by all Open Source project owners and maintainers, especially @weavejester who has created so many great projects for Clojure.

I didnt write a lot of code today, but felt I learnt some really invaluable information.  It also feels good to give back to an open source project, no matter how big or small the contribution.

Not having to concern myself with a delivery date for my project allowed me the feedom to dive into the projects and tools I have been using for quite a while.  This has given me a much better understanding of how to get the most out of them and help me teach other developers how to use them.  It is also way more fun.


### Code from today

I submitted a [pull request](https://github.com/weavejester/compojure-template/pull/25) to update the each library dependency to their latest stable version in the compojure-template.


### Activities in detail

Here is what I got up to in a lot more detail.


#### compojure-template pull request

When creating a new project from the [compojure-template]() yesterday I noticed that the version of libraries used in the template were a little dated.  Those versions stil work, but I decided to create a pull request with the latest stable versions of those libraries.

https://github.com/weavejester/compojure-template/pull/25

There was an existing pull request to update the libraries dependencies, however, that was also out of date.

The compojure-template project only describes how to run a generated project using the lein-ring plugin, using `lein ring server`.  The [lein-ring](https://github.com/weavejester/lein-ring) project readme describes [how to run the project from the Java command line](https://github.com/weavejester/lein-ring#executable-jar-files), but there is no reference to this information on the [compojure-template](https://github.com/weavejester/compojure-template/) project.  Again, I spotted a [pull request](https://github.com/weavejester/compojure-template/pull/23) to add these details to the readme so I added a thumbs up reaction with hope the maintainer will accept the pull request.


#### Digging deeper into lein-ring plugin

It is common in Clojure projects to define a `-main` function that is the start point to running the application.  However, the compojure-template doesnt generate a project with a `-main` function, instead it defines a Var called `app` that is the start of our application.

The reason for this approach is so that the compojure application can be packaged into a Java Web Archive (WAR) file and dropped into an existing Java Application Server (Tomcat, Jett, etc.).  This is the traditional approach to deploying a JVM webapp.

The lein-ring plugin adds a task called `ring` to Leiningen, so you can start the application on the command line using

```
lein ring server
```

Running the compojure project using lein-ring plugin starts an embedded Jetty web application server and passes the `app` to that running process to start listening for http requests.


#### Running as a stand alone application

With the rise in Cloud computing it is more common to run each application in its own embedded server, rather than deploying mulitple apps on a single applicaton server.  This new approach enables vertical scaling and parallel processing, something Clojure is an excellent language for.

Rather than write our own `-main` function to call Jetty, we can ask lein-ring plugin to do it for us.  A `-main` function is boilerplate code after all.

Use the lein-ring version of `lein uberjar` to generate a JAR file

```
lein ring uberjar
```

Taking a look at the contents of the generated JAR file we can see the additions made by the plugin.

> I use Spacemacs to open the Jar file as it will list all the files and let me read each text file it contains.

An application entry point has been added to the `meta-inf/manifest.mf` by specifying `Main-Class: status_monitor.handler.main`

Hold on though... we didnt have a `main` namespace in our code, so how does that work?

Well, lein-ring had created a file for that namespace with a `-main` function within it.  Here is the code contained within this automatically generated namespace.

```
(do
  (clojure.core/ns status-monitor.handler.main
    (:gen-class))

  (clojure.core/defn -main []
    ((do
       (clojure.core/require (quote ring.server.leiningen))

       (clojure.core/resolve (quote ring.server.leiningen/serve)))
     (quote {:ring
             {:handler status-monitor.handler/app,
              :open-browser? false,
              :stacktraces? false,
              :auto-reload? false,
              :auto-refresh? false}}))))
```

The code requires the namespace `ring.server.leiningen` so ic can run the `serve` function that takes the `app` as an argument.  `serve` will run an embedded jetty server and run our `app` within.

As `uberjar` is typically used to deply your application to a remote server (e.g. uat, production), then development features are set to false.  We dont really want a browser window to be opened when we run the app on a production server.

------------------------------------------

## 20180915 - Day 1: Staus Monitor mock website (server side) -

Started a simple status monitor application to collate monitoring information from different sources into one simple web dashboard.

### Thoughts from today

The compojure template is easy to get started with, it just works with the help of the `lein-ring` plugin.  The plugin takes the app defined in the `src/status_monitor/handler.clj` file and passes it to an embedded Jetty application server.  The plugin abstracts this detail away, making the project easy to run and less code to write.

This abstraction does make it a little harder to understand how this application actually runs and there is a lack of information on the template website.

### Code from today
https://github.com/jr0cket/webapp-status-monitor


### Details of today's activites

Started a new project using the Leiningen [compojure-template](https://github.com/weavejester/compojure-template)

```bash
lein new compojure status-monitor
```

This created a project using the `ring` and `compojure` libraries and Clojure 1.8.0

```clojure
  :dependencies [[org.clojure/clojure "1.8.0"]
                 [compojure "1.5.1"]
                 [ring/ring-defaults "0.2.1"]]
```

The project was updated to use the creative commons licence, rather than the deffault Eclipse public license which has is more restrictive.

Version 1.9.0 is now the current stable version of Clojure, so that has been updated in the dependencies.


The lein-compojure template is very simple to get started with, although it seems the libraries are a little behind the latest.  The project runs successfully without upgrading versions.  It is usually better to use the latest stable versions of these libraries to pick up any fixes.

The latest stable versions were found via https://clojars.org/.

> Consider submitting a pull request to update the lein-compojure template project on Github.


#### Running the REPL from Spacemacs

Although the project runs well from the command line using the `lein-ring` plugin, we dont get the full benefit of the REPL until we connect our editor to the REPL.  With the Compojure template you need to run the repl from Spacemacs as there is no way to connect to the REPL port from Spacemacs when the project is run with `lein ring server`.

Using the keybinding `, '` is a quick way to start the repl in Spacemacs.

#### Enhancing the webpage

The website is a litle basic in terms of output, so I added Bootstrap CSS and JavaScript libraries to the project as a simple way to make the output look a little more professional.

To use Bootstrap easily and avoid writing lots of html code, I used the Hiccup library.  Hiccup allows you to generate html code from Clojure vectors that contain Clojure keywords representing html tags.  Generating an html `h1` header and its text is written as `[:h1 "I am an HTML header"]`.

Using Clojure syntax in this way, makes it much easier to type.  Using this syntax also makes it easy to use structured editing with your code.

The project needs to include Hiccup library as a dependency.  Using the `clj-refactor` tools in Emacs, I added the hiccup dependencies and also hotloaded it into the already running repl.

### Added Hiccup and Bootstrap to create a better web page

Created the basics of our monitor dashboard page without writing html direct.

Added the Hiccup library to generate html from Clojure data structures and
keywords.

Using the hiccup.page/html5 function we created a page that allows us to include
the Bootstrap CSS and JavaScript libraries.  Hiccup allows us to include CSS
styles in the data structures, or more usefully refer to the Bootstrap styles by
name.

------------------------------------------

## 20180914 - Day 0: 14th September, 2016

Test out my development environment is working.  For the exercises I will be using Spacemacs, a community configuration for Emacs that also provides a comprehensive set of Vim states (Evil mode) that make editing code more effective.

Spacemacs is configured to use the Clojure layer, which pulls in CIDER packages, providing a comprehensive Clojure development environment that is equivalent to the features of an IDE without the resource requirements.

I will use Spacemacs for all coding and documentation for this 100 days challenge.  Along the way I will document my usage of Spacemacs and useful practices in the online guide: [Practicalli Spacemacs](https://practicalli.github.io/spacemacs).


### Today's Progress
As today is just a check of my environment, then no progress to report yet.

### Thoughts
I am a little nervous about this challenge as it will demonstrate just how much coding skill I currently have. My imposter syndome is kicking in a little as I think about it.  However, the excitement of emersing myself in Clojure coding for 100 days is over-riding this nervousness and hopefully this will continue to the end of the challenge.


### Link to work
[Practicalli Spacemacs](https://practicalli.github.io/spacemacs)
[My Github repository for 100 Days Of Clojure Code](https://github.com/jr0cket/100-days-of-clojure-code)
