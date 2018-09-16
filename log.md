# 100 Days Of Code - Log




### Day 1: Staus Monitor mock website (server side)
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
