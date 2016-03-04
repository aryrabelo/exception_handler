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
  <img src="/readme/branded/tsla.jpg" width="425" title="Fully Branded Error Pages" /> <img src="/readme/branded/sgm.jpg" width="425" title="Fully Branded Error Pages" />
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

**`ExceptionHandler`** works directly on the [**`ActiveDispatch::ShowExceptions`**](https://github.com/rails/rails/blob/4-0-stable/actionpack/lib/action_dispatch/middleware/show_exceptions.rb) middleware:

<p align="center">
  <img src="/readme/test.jpg" title="Exceptions handled by the ActiveDispatch::ShowExceptions Middleware" />
</p>

By catching exceptions with the [`config.exceptions_app`](http://guides.rubyonrails.org/configuring.html#rails-general-configuration) hook, **ExceptionHandler** invokes our `ExceptionsController` directly, removing *all* overhead:

> **`config.exceptions_app`** sets the exceptions application invoked by the **`ShowException`** middleware when an exception happens. Defaults to **`ActionDispatch::PublicExceptions.new(Rails.public_path)`**.

<p align="center">
  <img src="readme/exceptions_app.jpg" title="Exceptions App" />
</p>

**ExceptionHandler** uses our custom middleware to extract *all* the exception data for the request. Not only is this the most succinct, efficient way to do this, it also allows you to customize the *entire* fault-recovery process.

It's completely unique - the **only** professional solution to catch, process & handle exceptions in Rails. Unlike other solutions - mostly directing requests to `routes` - **ExceptionHandler** sends requests directly to the controller. 

----------

<p align="left">
  <img src="/readme/1clickinstall.jpg" title="1 Click Install" />
</p>

- [**Installation**](#installation)
- [**Development**](#testing)
- [**Bugs**](#bugs)
- [**Support**](#support)
  - [Video](#video)
  - [Issue](https://github.com/richpeck/exception_handler/issues)
  - [StackOverflow](http://stackoverflow.com/questions/ask?tags=exception_handler&ruby_on_rails)
- [**Roadmap**](#roadmap)
  - [0.5.0](#050)
  - [0.4.7](#047)
- [**Contribution**](#contribution)

----------

30,000 users can't be wrong (Rubygems)

ExceptionHandler has been **completely reworked** for `Rails 5`:





----------

<img src="readme/titles/roadmap.jpg" id="roadmap" />

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

----------