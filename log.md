# 100 Days Of Code - Log



## 20180929 - Day 15: Coaching ClojureBridge London

### Thoughts for today

I get a wonderful warm feeling when helping people get into the software industry, especially when its addressing the balance of voices in that industry.  To be able to help those new to development using my favourite language, Clojure, makes it extra special.

Clojure is quite different from most languages, specifically in the way it encourages you to think about the design of your code.  The simplicity that is achievable with Clojure is something that continues make me smile every day, even after 8 years of learning and working with Clojure.

The ClojureBridge event had over 20 women enjoying the day.  Six women already had some experience coding and one of them had just found out they had got their first job in the industry.  The rest of the students were very new.  Everyone was very excited about the day and that enthusiasm carried on throughout the day.


### Code from today

* The student wrote the code today, using examples from my status-monitor app and examples on stackoverflow.

### Activities in detail

I was coaching 4 women who had some coding experience.  Two of them had completed the first 6 levels of the workshop exercise in the afternoon and started building websites using Clojure.

Each student took a slightly different approch.  One student followed my [Practicalli Clojure WebApps]() step by step guide to building a server side web application with ring and compojure.  The second student used the [leiningen compojure template]() to start building a server side website that calculated the distance between two cities.

With the project created, we started the server with `lein ring server` to check it all worked.  To start building the page we added the [hiccup]() library, allowing us write an html web page using just Clojure code.  The `hiccup.page/html` function creates a web page and we define a `[:head ]` section that contains `include-css` and `include-js` functions so we can add bootstrap to our website and use some simple styles to make the site look better.

The data for the countries was defined within a Clojure map, e.g. `{:city "London" :latitude 51.5074 :longtitude 0.1278}`.  We added a dozen cities as maps to a Clojure vector and bound that vector to the symbol `locations`.

To select the cities from the web interface, we added a `form-to` function that included two input drop-downs.  Using a `for` statement we iterated over the `locations` collection and extracted the city name, placing it into the drop down.  This gave us a to and from location to select.

Using the submit button to call a results page, we extracted the selected cities from the request params.  Then called a function that calculated the distance between two locations using their respective latitude and longtitude positions.


------------------------------------------


## 20180928 - Day 14: Hacking ClojureBridge London

### Thoughts for today

Running our 8th ClojureBridge London event to support under represented groups gain experience and build confidence when it comes to codeing.

Updated some of the ClojureBridge content and examples.

Some ClojureX conference management.


### Code from today

* https://github.com/ClojureBridgeLondon/workshop-content-gitbook/commits/master

### Activities in detail


------------------------------------------

## 20180927 - Day 13: Demo-graphics continued

### Thoughts for today

Some more user research.  Buiding websitest that tell you something isnt as easy as it seams.

Making good used of Layouts in Spacemacs to organise my work more effectively.

Continued with building up the SVG library

### Code from today

* https://github.com/jr0cket/webapp-status-monitor/commit/940ec90df0ef87cd69fce7f9e9859c7dfd75488b

### Activities in detail

More hacking on the SVG library I have been working on in the status-monitor app.  Continuing to define example SVG elements in Clojure.


------------------------------------------

## 20180926 - Day 12: Demo-graphics

### Thoughts for today

More experimenting with SVG and included some simple HTML.  At some stage will need to decide what styles to include inline for HTML elements, what to include as templates and what to define as CSS (and any other / additonal css libraries to use).

### Code from today

* Demos with SVG and HTML
https://github.com/jr0cket/webapp-status-monitor/commit/93189468fc80938865fb67f4ff6de77f9d4bc724

### Activities in detail

Hacking with more SVG graphics and wrapping those graphics with HTML.

Debugging the html output is very easy with the Chrome Inspector.

------------------------------------------

## 20180925 - Day 11: Diversity is a balancing act

### Thoughts for today

Today was distracted with issues raised around this years ClojureX conference.  Although we strive to get as much balance as possible in the speakers for our annual conference and the last few years have been quite successful, unfortunately we only have a few women speakers confirmed this year.  We spend time reaching out to under represented groups and supporting them in many ways to get involved with the conference.  We do reach out to speakers we want to appear at the conference and this also has a bias to ensure we have a good balance.  Although we have been very successful encouraging new speakers to the conference, the representation of those new speakers has not been as broad this year.  One of our speakers pulled out of the conference as they understandably felt it was not appropriate to speak, especially as they were pair presenting with a colleague who would have contributed to the balance we strive to achieve.  Luckily the speaker had two other colleagues who would bring the same balance that we were hoping for.

Unfortunately this took up most of the day today and didnt leave much time for coding before heading off to run the Coding dojo at Thoughtworks.  Unfortunately Yolina who has done a wonderful job of running these events for the last few years was ill. I hope Yolina a swift recovery.

The Clojure code dojo was lots of fun tonight.  We had 3 groups of people fairly new to Clojure, working through lots of 4clojure.com exercises.  We also had a group creating a notification app for the Park Run events.  Unfortunately this popular site does not have a published API, so lots of webscraping with the enlive library was in order.  I spent most of the time coaching the teams through the 4Clojure exercises, helping them to think in a functional way.  We also had a very interesting discussion around functional design patterns and what if any were the relationships between functional and OO patterns.  Our conclusion being that most of the OO patterns provide features that are not available in the language.  Understanding functional design or patterns is more about understanding the Clojure (or Lisp) style of functional programming and what is the so called `idiomatic` approach to Clojure.

I still managed to get some time to work on the Status Monitor, although this was more about defining SVG elements and considering creating a library of SVG components to make it easier to incorporate them in Clojure or ClojureScript projects.

The day ended on a high note with my pull request to the Compojure Leiningen template merged by @weavejester


### Code from today

* Compojure template pull request merged
https://github.com/weavejester/compojure-template/pull/25

* SVG components namespace with a simple demo
https://github.com/jr0cket/webapp-status-monitor/commit/427c56c5ce5e7c516955d34daa32f49cb3893d79


### Activities in detail

Not much coding today, so no real detail to cover.

Created a new namespace in the status-monitor application for svg-components.  Planning to start converting the [Mozilla SVG guide](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Getting_Started) and [SVG Elements Reference](https://developer.mozilla.org/en-US/docs/Web/SVG/Element)



------------------------------------------


## 20180924 - Day 10: Mocking has never been easier

### Thoughts for today

Refined the tests using the `ring.mock.request` mocking library that Compojure Leiningen template added when creating the project.


### Code from today

* Refactor test to use ring.mock.request
https://github.com/jr0cket/webapp-status-monitor/commit/a71781610e800f524ce46dfdb0e18653aea19c2d

### Activities in detail

#### Refining the tests with ring.mock.request

The test from yesterday was not quite as elegant as it could be.  Although it showed clearly what it was testing, there was much duplication.

```clojure
#_(deftest test-monitor-dashboard
  (testing "Test dashboard contains key pieces of information"
    (is (clojure.string/includes?
         (monitor-dashboard {})
         "<title>Area51 Mock Status</title>"))
    (is (clojure.string/includes?
         (monitor-dashboard {})
         "<link href=\"//stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css\" rel=\"stylesheet\" type=\"text/css\">"))
    (is (clojure.string/includes?
         (monitor-dashboard {}) "<div class=\"jumbotron\"><h1>Mock Status Monitor Dashboard</h1></div>"))
    (is (clojure.string/includes?
         (monitor-dashboard {}) "<h2>Application monitor</h2>"))
    (is (clojure.string/includes?
         (monitor-dashboard {})
         "view-box=\"0 0 100 20\""))))
```


I refactored the above test to use a let function to create a local binding called response, bound to the value of calling the webapp route `/dashboard`.  This testing the correct flow of our webapp route and its response.

The let name `response` was bound to the `/dashboard` response by calling `(app (mock/request :get "/dashboard"))` from the `ring.mock.request` mocking library.

The response is a Clojure map which has a key called `:body` that contains the html output for the web page.  So I extract the value using the `:boot` key.

Added `clojure.string` to the namespace with an alias `string` so I could simply call `string/includes?` instead of `clojure.string/includes?`.  I could refer `includes?` into the namespace, however, I prefer to be explicit in the use of libraries (unless there is extensive use of specific functions in a namespace that is focused on the context of those functions, i.e. a UI namespace that uses Hiccup).

So, the refactored test now looks a little more streamlined.

```clojure
(deftest test-monitor-dashboard
  (testing "Test dashboard contains key pieces of information"
    (let [response (app (mock/request :get "/dashboard"))]
      (is (= (:status response) 200))

      (is (string/includes?
          (:body response)
           "<title>Area51 Mock Status</title>"))
      (is (string/includes?
           (:body response)
           "<link href=\"//stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css\" rel=\"stylesheet\" type=\"text/css\">"))
      (is (string/includes?
           (:body response) "<div class=\"jumbotron\"><h1>Mock Status Monitor Dashboard</h1></div>"))
      (is (string/includes?
           (:body response) "<h2>Application monitor</h2>"))
      (is (string/includes?
           (:body response)
           "view-box=\"0 0 100 20\"")))))
```

------------------------------------------

## 20180923 - Day 9: Testing is fun

### Thoughts for today

More testing today and taking a brief look at the mocking framework that Compojure Leiningen template added to the test code generated.

Also has a quick look at eftest from @weavejester which is supposed to be faster and can run more tests in parrallel than just running `lein test`.  I mainly wanted to use it for the coloured output at this stage (as I only have a few tests).

By accident I found the Emacs transpose keybinding is still in Spacemacs today. Instead of pressing `M-TAB` I was pressing `M-t` and swapping around the two words either side of the cursor position.  The transpose call even jumps over and ignores comments and other separators.

The standard Spacemacs bindings for transpose are as follows:

* `SPC x t c`	swap (transpose) the current character with the previous one
* `SPC x t w`	swap (transpose) the current word with the previous one
* `SPC x t l`	swap (transpose) the current line with the previous one

This is something else to add to my [Spacemacs for Clojure development guide](https://practicalli.github.io/spacemacs).

### Code from today

* Added eftest plugin
https://github.com/jr0cket/webapp-status-monitor/commit/b5f8b2a83ce9839c7881b4a5b80d8d7911b13fb2

* Added tests for monitor dashboard
https://github.com/jr0cket/webapp-status-monitor/commit/d2016c004b9122677986f3933270e900ce59d0a8

* Added author and documentation to test namespace
https://github.com/jr0cket/webapp-status-monitor/commit/f5eed17e129ffd2e6c402d1292fb900164129259

* Experimenting in the REPL
https://github.com/jr0cket/webapp-status-monitor/commit/bfa92e18ebb5b57c223c6b6851277ee88c1819c7

* Updated the Readme to include an ascii text logo
https://github.com/jr0cket/webapp-status-monitor/commit/f8b6bef2486fc972e0f82599b9303c0616ef5195


### Activities in detail

#### Adding an ascii text logo

Perhaps a little superfluous but an easy thing to add is an ascii text logo of the project name.  I use the [text to ascii art generator (TAAG)](http://patorjk.com/software/taag/#p=display&f=Fire%20Font-k&t=status%20monitor) and the Fire Font.

The output of the generator was copied into a text block in the project README.md file.

#### REPL experiement - calling monitor-dashboard function

Confirming the output of the monitor-dashboard function by calling that function via the REPL, using an empty map {} as the function argument.

The monitor-dashboard is currently passive and so does not use any data from the request map.

If the monitor-dashboard function did use data from the request map, we would need to mock that in the call to monitor-dashboard.

#### Testing monitor-dashboard

Using clojure.string/includes? to see if the result of calling the monitor-dashboard function includes specific sub-strings.

This could be done using the mock framework and put into a let to make the code cleaner.

```clojure
(deftest test-monitor-dashboard
  (testing "Test dashboard contains key pieces of information"
    (is (clojure.string/includes?
         (monitor-dashboard {})
         "<title>Area51 Mock Status</title>"))
    (is (clojure.string/includes?
         (monitor-dashboard {})
         "<link href=\"//stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css\" rel=\"stylesheet\" type=\"text/css\">"))
    (is (clojure.string/includes?
         (monitor-dashboard {}) "<div class=\"jumbotron\"><h1>Mock Status Monitor Dashboard</h1></div>"))
    (is (clojure.string/includes?
         (monitor-dashboard {}) "<h2>Application monitor</h2>"))
    (is (clojure.string/includes?
         (monitor-dashboard {})
         "view-box=\"0 0 100 20\""))))
```

Tomorrow I'll refactor the above test to use a `let` value for the response from calling monitor-dashboard. I will also use the `(app (mock/request :get "/"))` call in the `let` and compare the `:body` from the response.


#### Added eftest plugin for pretty results report

[eftest](https://github.com/weavejester/eftest) provides a faster testing tool and syntax coloured reporting of results, making it nicer to use that `lein test`.

Run the tests using the eftest plugin on the command line using `lein eftest`

The plugin uses several dependencies

[Clojure Leiningen eftest plugin dependencies](/images/clojure-testing-eftest-dependencies.png)

The output in this test run that contains two test failures is very clear to understand and spot the issues easily.

[Clojure Leiningen eftest plugin - failing test run](/images/clojure-testing-eftest-test-run-failures.png)


------------------------------------------


## 20180922 - Day 8: Clojure coaching and Testing

### Thoughts for today

Started coaching a developer today.  It has been a few months since I coached, so am happy to be starting again.  Coaching really does help me exercise my mind and it is very enjoyable to guide someone.

One decision taken in the coaching was which continuous integration server to use.  I realised I should start writing some tests and set up a CI server for the status monitor project.  The simplest approach for a CI server was to use [CircleCI](https://circleci.com/) that provides CI as a service and hooks up easily to Github projects.  CircleCI is also written in Clojure, so its great to support them.


### Code from today

Added tests for components
https://github.com/jr0cket/webapp-status-monitor/commit/2647704466ea05c3fb6ba3eba46fa28d341000e7

Updated the Readme and added CircleCI status badge
https://github.com/jr0cket/webapp-status-monitor/commit/f7912e1e8151b3c399bd3c4e517d3a7d11709f8e


### Activities in detail

#### Setting up CircleCI for the status-monitor project

There is a really good [getting started guide](https://circleci.com/docs/2.0/getting-started/) on the CircleCI website.

Adding a project and CircleCI detects the programming language and your operating system.

[![CircleCI](/images/circleci-add-project-detection.png)](/images/circleci-add-project-detection.png)

Added the sample `config.yml` to the project as `.configci/config.yml`.  The only change made to the config file was to update the version of Leiningen to 2.8.1 (was version 2.7.1).  Once this was added to the project and pushed up to the github repostitory, then we are ready to create a build.

This launches the project on CircleCI and webhooks listen for new commits to the Github repostitory.

Adding a [status badge](https://circleci.com/gh/jr0cket/webapp-status-monitor/edit#badges) to the Github readme was very simple too.  CircleCI provides the Markdown to add to the README.md page.


#### Testing status-monitor

The Compojure template comes with a few tests that nicely show how to group tests and give some hints on things to test.

Started adding tests to check the output generated by the visual components I am developing to represent the elements of the dashboard.


#### Coaching

I created a Slack community specifically for the coaching, so we can keep our discussions around for several months if required.  We discussed what was to be achieved (at least initially) from the coaching, tooling and development experiences.


------------------------------------------

## 20180921 - Day 7: Clojure advocacy and Spacemacs

### Thoughts for today

This morning I had a great conversation with an exciting company that is looking to move to Clojure for key computational parts of their systems.  Lots of discussion centred around finding and hiring Clojure developers, for which there are many options.

The rest of the day was spent working on my book [Spacemacs for Clojure development](https://github.com/practicalli/spacemacs-gitbook/).

### Code from today

Content and elisp code snippets for my Spacemacs book:
https://github.com/practicalli/spacemacs-gitbook/

### Activities in detail

I have been steadily creating content for my book to help developers make the most out of Spacemacs for Clojure development.  There is still much content to go, however, there is lots of really useful things I have learnt and added over the last few weeks.

I have also been adding more content ideas in the [Github project for the book](https://github.com/practicalli/spacemacs-gitbook/projects/1).

------------------------------------------

## 20180920 - Day 6: ClojureBridge London


### Thoughts for today

Preparing for the ClojureBridge London event next weekend by reviewing the workshop content and enhancing some of the challenges and sample answers.

Also carried out some user research for developer portals of several financial institues.  There was definately a large difference in usability and developer experience between the sites reviewed.  Hopefully my comments are of some contructive use and I wasnt overly critical.

### Code from today

Code examples and content for the ClojureBridge London workshop
https://github.com/ClojureBridgeLondon/workshop-content-gitbook

### Activities in detail

Improved several sections of the ClojureBridge workshop content.

------------------------------------------

## 20180919 - Day 5: A very Googley day - Alexa, Android and Googling answers


### Thoughts for today

I was at an Amazon for an Alexa workshop building what they refer to as _skills_, their word for defining the things that you can configure Alexa to do.  It was good fun, very well explained and I also won an Echo dot (which should arrive in the post tomorrow).

This evening I coached at [Codebar](https://codebar.io), helping a very bright person with their Augmented Reality application for Android which was written in Kotlin.  I can see why experienced Android developers are able to get a great rate for their work, as it feels like a lot of moving parts to build such a native app.  They managed to get further with the app and we even got some UI tests instrumented.

Not progress on the Clojure app today, although had a very interesting talk about the need to do more to highlight what makes Clojure so special.  I did do some work on this for ClojureBridge London workshop https://clojurebridgelondon.github.io/workshop/introducing-clojure/


### Code from today

AWS Lambda function for several Alexa skills:
https://github.com/jr0cket/aws-lambda-jenkins-deployer-alexa/commit/5e601b817c812549104d1a8f14ce7ade23c6c5f9

### Activities in detail

#### Alexa Workshop

To make voice work, the service needs to understand millions of words so that it can accurately interpret what you are saying and have a better chance of doing the right thing.  If Alexa doesunt understand the words you say, then its not going to do what you want.

The Alexa Framework can be used to enable any device, not just the devices from Amazon.

They are called skills (rather than voice apps) as we are teaching Alexa to do something specific.


------------------------------------------

## 20180918 - Day 4: Are you mocking me :)

Today was a great meetup at Signal Media.  Talked about the #100daysofcode challenge I am doing and the experiments with Scalable Vector Graphics. Discussed the case for ClojureScript and Reagent over JavaScript and React.js

Also helped someone on Clojurians Slack write a keybinding for [lispy]() functions `lispy-pair` and `lispy-quote` that did not have keybindings defined in the package.  Lispy is an alternative to Evil and Smartparents and whilst interesting, its not something I am inclined to try myself.

### Thoughts for today

There are so many companies using Clojure I keep finding out about.  The TV company Vue.tv uses Clojure for all their data processing around their broadcasting business.

GraphQL in a lambda works surprisingly well according to Alex's talk.  That was really interesting.

### Code from today

https://github.com/jr0cket/webapp-status-monitor/commit/1c282057c2d1a7433a36ad50b2845c79e788f128

### Activities in detail

#### Mock data generators

I'd like to test out the SVG dashboard with a number of different data sets.  Rather than just type a lot of random numbers into the code, I wrote a mock-data generator function.  This mock data first returned float values.


```
(defn mock-data
  "Mock data generator"
  [maximum-value]
  (rand (+ maximum-value 1)))
```

The `mock-data` function was refactored to generate either float or integer random data based on the type passed to the `mock-data` function as an argument.

gAs the float generated number has multiple decimal places and we only want two for the display, the `format` function is used to limit the precision of the returning number to 2 decimal places.

```(defn mock-data
  "Mock data generator"
  [maximum-value]
  (if (float? maximum-value)
    (format "%.2f" (rand (+ maximum-value 1)))
    (rand-int (+ maximum-value 1))))
```


#### Joker linter

As I was experimenting with a mock-data generator in the REPL experiments section, I noticed that Joker reports out of order issues.  So it will highlight if you try to call a function before its defined in the file.  This happens even if the function has already been evaluated in the repl.  This situation does remind me that Joker reads the whole Clojure file each time a change is made.

I am finding Joker invaluable to guard against very silly mistakes and thus avoiding hunting through code for silly mistakes.

More Joker awesomenessness.

------------------------------------------

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
