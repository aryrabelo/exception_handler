![Exception Handler](/readme/title.jpg "Exception Handler Logo")

<p align="center">
  <a href="http://badge.fury.io/rb/exception_handler"><img src="https://badge.fury.io/rb/exception_handler.svg"></a>
  <a href="https://codeclimate.com/github/richpeck/exception_handler"><img src="https://codeclimate.com/github/richpeck/exception_handler.png"></a>
  <a href="https://gemnasium.com/richpeck/exception_handler"><img src="https://gemnasium.com/richpeck/exception_handler.svg"></a>
  <a href="https://coveralls.io/r/richpeck/exception_handler"><img src="https://coveralls.io/repos/richpeck/exception_handler/badge.png"></a>
  <a href="https://travis-ci.org/richpeck/exception_handler"><img src="https://travis-ci.org/richpeck/exception_handler.svg?branch=master"></a>
</p>

----------

**ExceptionHandler** helps you can create custom **404 & 500 production error pages** *(adapted from [**1**](https://gist.github.com/wojtha/8433843) & [**2**](http://www.sharagoz.com/posts/1-rolling-your-own-exception-handler-in-rails-3))*.

![Exceptions_App middleware](/readme/subtitle.jpg)

**ExceptionHandler** is the *only* production-ready custom error page solution for Rails 4 & 5. 

---

<p align="center">
  <br /><img src="/readme/05_title.png" width="450" /><br/>
  <strong>Customize <i>404</i> and <i>500</i> error pages to be branded to your application in production:</strong>
</p>

<p align="center">
  <img src="/readme/check.png" height="22" title="Fully Responsive"               align="absmiddle" />&nbsp; Responsive &nbsp;
  <img src="/readme/check.png" height="22" title="Branded Error Pages"            align="absmiddle" />&nbsp; Branded Error Pages &nbsp;
  <img src="/readme/check.png" height="22" title="Middleware Exception Handling"  align="absmiddle" />&nbsp; Middleware Exception Handling &nbsp;
  <img src="/readme/check.png" height="22" title="Keep Users Informed"            align="absmiddle" />&nbsp; Fully Customizable &nbsp;
</p>

<p align="center">
  <img src="/readme/branded/tsla.jpg" width="425" title="Fully Branded Error Pages" /> <img src="/readme/branded/tsla.jpg" width="425" title="Fully Branded Error Pages" />
  <img src="/readme/branded/tsla.jpg" width="425" title="Fully Branded Error Pages" /> <img src="/readme/branded/tsla.jpg" width="425" title="Fully Branded Error Pages" />
</p>

This is the most feature-rich, stable & effective solution for **custom error pages** in Rails 4 & 5.

---

<p align="center">
  <img src="/readme/05.jpg" title="Version 0.5" width="450" />
</p>

--- cultivate your brand

**ExceptionHandler** uses `config.exceptions_app` to catch errors & send them to the [`exceptions` controller](app/controllers/exception_handler/exception_controller.rb).

Tapping directly into the data stored in `Rack` (`message`, `details`, `user agent`), **ExceptionHandler** populates your own `custom view`, sending data to the DB & email notifications of the error:

<div align="center">
  <img src="/readme/400.jpg" title="400 Errors" width="435" />
  <img src="/readme/500.jpg" title="500 Errors" width="435" />
</div>

---

Rails exceptions are handled by the [**`ActiveDispatch::ShowExceptions`**](https://github.com/rails/rails/blob/4-0-stable/actionpack/lib/action_dispatch/middleware/show_exceptions.rb) middleware:

<p align="center">
  <img src="http://www.whynot.io/images/rack-in-ruby/rack-does-exist.png" title="Exceptions handled by the ActiveDispatch::ShowExceptions Middleware" />
</p>

By catching exceptions with the [`config.exceptions_app`](http://guides.rubyonrails.org/configuring.html#rails-general-configuration) hook, **ExceptionHandler** invokes our `ExceptionsController` directly, removing *all* overhead:

> **`config.exceptions_app`** sets the exceptions application invoked by the **`ShowException`** middleware when an exception happens. Defaults to **`ActionDispatch::PublicExceptions.new(Rails.public_path)`**.

<p align="center">
  <img src="readme/exceptions_app.jpg" title="Exceptions App" />
</p>

**ExceptionHandler** uses our custom middleware to extract *all* the exception data for the request. Not only is this the most succinct, efficient way to do this, it also allows you to customize the *entire* fault-recovery process.

It's completely unique - the **only** professional solution to catch, process & handle exceptions in Rails. Unlike other solutions - mostly directing requests to `routes` - **ExceptionHandler** sends requests directly to the controller. 

----------

<img src="/readme/install.jpg" title="One Click Install" width="400" align="right" />

<p align="left">
  <br />
  <img src="/readme/titles/1clickinstall.jpg" title="1 Click Install" />
</p>

- [**Installation**](#installation)
- [**Development**](#testing)
- [**Bugs**](#bugs)
- [**Support**](#support)
  - [Video](#video)
  - [Issue](https://github.com/richpeck/exception_handler/issues)
  - [StackOverflow](http://stackoverflow.com/questions/ask?tags=exception_handler&ruby_on_rails)
- [**Changelog**](#changelog)
  - [0.5.0](#050)
  - [0.4.7](#047)
- [**Contribution**](#contribution)

----------

## Installation

     gem install 'exception_handler'
 
or 

    #Gemfile
    gem 'exception_handler', '~> 0.5.0'

30,000 users can't be wrong (rubygems)

Create professional-grade applications with the help of **Rails custom error pages**.

----------

##### Config

If you wish to change any of the default settings (below), you should now add `config.exception_handler` to your `config/application.rb` or `config/production.rb` file:

![Config Options](/readme/config.jpg)


**IMPORTANT**

If you're upgrading from `>= 0.4.7`, you need to **remove your `exception_handler` initializer**.

We've changed the load process to use Rails app `config` - **you don't need the `exception_handler` initializer any more** ([more](https://github.com/richpeck/exception_handler/wiki/Setup))

----------

##### DB

If you want to store exceptions in the db, you will need to set up a `migration`:

    $ rails generate exception_handler:migration
    $ rake db:migrate

![Database](/readme/db.jpg "Database")

You will also need to ensure your config `db` option is either `true` || `:table_name`:

![Database Edit](/readme/db_edit.jpg "Database Edit")

----------

##### Views

If you want to change the views, you can have them put into your app:

    $ rails generate exception_handler:views                                            #-> controller, models, helpers, views & assets
	  $ rails generate exception_handler:views -v views controllers models helpers assets #-> remove as appropriate to install individual assets


![Layout](/readme/layout.jpg "Layout")

----------

<img src="/readme/titles/testing.png" id="development" />

**`Exception Handler`** now supports a rigorous test suite:

---

##### Development

`config.exceptions_app` is only used in Rails' **production** environment.

If you wish to customize in dev, you need to make your app process requests as production. This is a temporary step, and will be resolved in a new version:

![#config/environments/development.rb](/readme/dev.jpg "Developer Testing")

You should change this setting if you wish to test your styling in development mode. It should be temporary (you need to change it back once you have it looking how you like)

----------

<img src="readme/titles/bugs.png" id="bugs" />

#### `ApplicationController`

   ![ApplicationController](/readme/application_controller.jpg "Application Controller")
   
   A significant issue exists in respect to the inheritance of `exceptions_controller`:
   

   If you use any sort of `before_action` callback in your controller, especially to populate variables, this
   will cause untold problems in your `exceptions_controller`. 

   `500` errors are server faults; trying to get the server to call more data will simply not work. It causes
   an exception loop, leading to catastrophic failure.


#### Routes

If you are using any custom routes in `application` layout, you need to prepend `main_app` to them:

----------

<img src="readme/titles/changelog.png" id="changelog" />

#### 0.5.0
 - Added locales
 - Email notifications
 - Full test suite (finally)
 - Rails 4.2 & Rails 5.0 native ([`request.env`](https://github.com/rails/rails/commit/05934d24aff62d66fc62621aa38dae6456e276be) fix)
 - Controller fixed
 - `DB` fixed
 - Legacy initializer support ([more](https://github.com/richpeck/exception_handler/wiki/Setup))
 - Rails asset management improvement
 - Cut out most dev files from gem (drastic reduction in gem size)


#### 0.4.7

 - New config system ([more](https://github.com/richpeck/exception_handler/wiki/Setup))
 - Fixed controller layout issues
 - Streamlined middleware
 - New layout & interface implementation


----------

<img src="readme/titles/support.png" id="support" />

#### Video

**Coming Soon**

[![Test Video](http://img.youtube.com/vi/GY7Ps8fqGdc/0.jpg)](http://www.youtube.com/watch?v=GY7Ps8fqGdc "Test Video")

#### [Issue](https://github.com/richpeck/exception_handler/issues)

**~60 minute response time**

#### [StackOverflow](http://stackoverflow.com/questions/ask?tags=exception-handler+ruby-on-rails) 

**~24 hour response time**

----------

<img src="readme/titles/contribution.png" id="contribution" />

Contributions welcome.

1. Fork it ( https://github.com/richpeck/exception_handler/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request