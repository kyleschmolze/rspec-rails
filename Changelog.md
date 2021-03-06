### 2.12.2 / 2013-01-12
[full changelog](http://github.com/rspec/rspec-rails/compare/v2.12.1...v2.12.2)

Bug fixes

* Reverts earlier fix where anonymous controllers defined the `_routes` method
  to support testing of redirection and generation of URLs from other contexts.
  The implementation ended up breaking the ability to refer to non-anonymous
  routes in the context of the controller under test.

### 2.12.1 / 2013-01-07
[full changelog](http://github.com/rspec/rspec-rails/compare/v2.12.0...v2.12.1)

Bug fixes

* Operates correctly when ActiveRecord is only partially loaded (e.g., with
  older versions of Mongoid). (Eric Marden)
* `expect(subject).to have(...).errors_on` operates correctly for
  ActiveResource models where `valid?` does not accept an argument. (Yi Wen)
* Rails 4 support for routing specs. (Andy Lindeman)
* Rails 4 support for `ActiveRecord::Relation` and the `=~` operator matcher.
  (Andy Lindeman)
* Anonymous controllers define `_routes` to support testing of redirection
  and generation of URLs from other contexts. (Andy Lindeman)

### 2.12.0 / 2012-11-12
[full changelog](http://github.com/rspec/rspec-rails/compare/v2.11.4...v2.12.0)

Enhancements

* Support validation contexts when using `#errors_on` (Woody Peterson)
* Include RequestExampleGroup in groups in spec/api

Bug fixes

* Add `should` and `should_not` to `CollectionProxy` (Rails 3.1+) and
  `AssociationProxy` (Rails 3.0).  (Myron Marston)
* `controller.controller_path` is set correctly for view specs in Rails 3.1+.
  (Andy Lindeman)
* Generated specs support module namespacing (e.g., in a Rails engine).
  (Andy Lindeman)
* `render` properly infers the view to be rendered in Rails 3.0 and 3.1
  (John Firebaugh)
* AutoTest mappings involving config/ work correctly (Brent J. Nordquist)
* Failures message for `be_new_record` are more useful (Andy Lindeman)

### 2.11.4 / 2012-10-14
[full changelog](http://github.com/rspec/rspec-rails/compare/v2.11.0...v2.11.4)

Capybara-2.0 integration support:

* include RailsExampleGroup in spec/features (necessary when there is no AR)
* include Capybara::DSL and Capybara::RSpecMatchers in spec/features

See [https://github.com/jnicklas/capybara/pull/809](https://github.com/jnicklas/capybara/pull/809)
and [http://rubydoc.info/gems/rspec-rails/file/Capybara.md](http://rubydoc.info/gems/rspec-rails/file/Capybara.md)
for background.

2.11.1, .2, .3 were yanked due to errant documentation.

### 2.11.0 / 2012-07-07
[full changelog](http://github.com/rspec/rspec-rails/compare/v2.10.1...v2.11.0)

Enhancements

* The generated `spec/spec_helper.rb` sets `config.order = "random"` so that
  specs run in random order by default.
* rename `render_template` to `have_rendered` (and alias to `render_template`
  for backward compatibility)
* The controller spec generated with `rails generate scaffold namespaced::model`
  matches the spec generated with `rails generate scaffold namespaced/model`
  (Kohei Hasegawa)

Bug fixes

* "uninitialized constant" errors are avoided when using using gems like
  `rspec-rails-uncommitted` that define `Rspec::Rails` before `rspec-rails`
  loads (Andy Lindeman)

### 2.10.1 / 2012-05-03
[full changelog](http://github.com/rspec/rspec-rails/compare/v2.10.0...v2.10.1)

Bug fixes

* fix regression introduced in 2.10.0 that broke integration with Devise
  (https://github.com/rspec/rspec-rails/issues/534)
* remove generation of helper specs when running the scaffold generator, as
  Rails already does this (Jack Dempsey)

### 2.10.0 / 2012-05-03
[full changelog](http://github.com/rspec/rspec-rails/compare/v2.9.0...v2.10.0)

Bug fixes

* `render_views` called in a spec can now override the config setting. (martinsvalin)
* Fix `render_views` for anonymous controllers on 1.8.7. (hudge, mudge)
* Eliminate use of deprecated `process_view_paths`
* Fix false negatives when using `route_to` matcher with `should_not`
* `controller` is no longer nil in `config.before` hooks
* Change `request.path_parameters` keys to symbols to match real Rails
  environment (Nathan Broadbent)
* Silence deprecation warnings in pre-2.9 generated view specs (Jonathan del
  Strother)

### 2.9.0 / 2012-03-17
[full changelog](http://github.com/rspec/rspec-rails/compare/v2.8.1...v2.9.0)

Enhancements

* add description method to RouteToMatcher (John Wulff)
* Run "db:test:clone_structure" instead of "db:test:prepare" if Active Record's
  schema format is ":sql". (Andrey Voronkov)

Bug fixes

* `mock_model(XXX).as_null_object.unknown_method` returns self again
* Generated view specs use different IDs for each attribute.

### 2.8.1 / 2012-01-04

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.8.0...v2.8.1)

NOTE: there was a change in rails-3.2.0.rc2 which broke compatibility with
stub_model in rspec-rails. This release fixes that issue, but it means that
you'll have to upgrade to rspec-rails-2.8.1 when you upgrade to rails >=
3.2.0.rc2.

* Bug fixes
    * Explicitly stub valid? in stub_model. Fixes stub_model for rails versions
      >= 3.2.0.rc2.

### 2.8.0 / 2012-01-04

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.8.0.rc2...v2.8.0)

* Enhancements
    * Eliminate deprecation warnings in generated view specs in Rails 3.2
    * Ensure namespaced helpers are included automatically (Evgeniy Dolzhenko)
    * Added cuke scenario documenting which routes are generated for anonymous
      controllers (Alan Shields)

### 2.8.0.rc2 / 2011-12-19

[full changelog](http://github.com/rspec/rspec-mocks/compare/v2.8.0.rc1...v2.8.0.rc2)

* Enhancements
    * Add session hash to generated controller specs (Thiago Almeida)
    * Eliminate deprecation warnings about InstanceMethods modules in Rails 3.2

* Bug fixes
    * Stub attribute accessor after `respond_to?` call on mocked model (Igor
      Afonov)

### 2.8.0.rc1 / 2011-11-06

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.7.0...v2.8.0.rc1)

* Enhancements
    * Removed unnecessary "config.mock_with :rspec" from spec_helper.rb (Paul
      Annesley)

* Changes
    * No API changes for rspec-rails in this release, but some internals
      changed to align with rspec-core-2.8

* [rspec-core](https://github.com/rspec/rspec-core/blob/master/Changelog.md)
* [rspec-expectations](https://github.com/rspec/rspec-expectations/blob/master/Changelog.md)
* [rspec-mocks](https://github.com/rspec/rspec-mocks/blob/master/Changelog.md)

### 2.7.0 / 2011-10-16

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.6.1...v2.7.0)

* Enhancements
  * `ActiveRecord::Relation` can use the `=~` matcher (Andy Lindeman)
  * Make generated controller spec more consistent with regard to ids
    (Brent J. Nordquist)
  * Less restrictive autotest mapping between spec and implementation files
    (Jos?? Valim)
  * `require 'rspec/autorun'` from generated `spec_helper.rb` (David Chelimsky)
  * add `bypass_rescue` (Lenny Marks)
  * `route_to` accepts query string (Marc Weil)

* Internal
  * Added specs for generators using ammeter (Alex Rothenberg)

* Bug fixes
  * Fix configuration/integration bug with rails 3.0 (fixed in 3.1) in which
    `fixure_file_upload` reads from `ActiveSupport::TestCase.fixture_path` and
    misses RSpec's configuration (David Chelimsky)
  * Support nested resource in view spec generator (David Chelimsky)
  * Define `primary_key` on class generated by `mock_model("WithAString")`
    (David Chelimsky)

### 2.6.1 / 2011-05-25

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.6.0...v2.6.1)

This release is compatible with rails-3.1.0.rc1, but not rails-3.1.0.beta1

* Bug fixes
  * fix controller specs with anonymous controllers with around filters
  * exclude spec directory from rcov metrics (Rodrigo Navarro)
  * guard against calling prerequisites on nil default rake task (Jack Dempsey)

### 2.6.0 / 2011-05-12

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.5.0...v2.6.0)

* Enhancements
  * rails 3 shortcuts for routing specs (Joe Fiorini)
  * support nested resources in generators (Tim McEwan)
  * require 'rspec/rails/mocks' to use `mock_model` without requiring the whole
    rails framework
  * Update the controller spec generated by the rails scaffold generator:
    * Add documentation to the generated spec
    * Use `any_instance` to avoid stubbing finders
    * Use real objects instead of `mock_model`
  * Update capybara integration to work with capy 0.4 and 1.0.0.beta
  * Decorate paths passed to `[append|prepend]_view_paths` with empty templates
    unless rendering views. (Mark Turner)

* Bug fixes
  * fix typo in "rake spec:statsetup" (Curtis Schofield)
  * expose named routes in anonymous controller specs (Andy Lindeman)
  * error when generating namespaced scaffold resources (Andy Lindeman)
  * Fix load order issue w/ Capybara (oleg dashevskii)
  * Fix monkey patches that broke due to internal changes in rails-3.1.0.beta1

### 2.5.0 / 2011-02-05

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.4.1...v2.5.0)

* Enhancements
  * use index_helper instead of table_name when generating specs (Reza
    Primardiansyah)

* Bug fixes
  * fixed bug in which `render_views` in a nested group set the value in its
    parent group.
  * only include MailerExampleGroup when it is defined (Steve Sloan)
  * mock_model.as_null_object.attribute.blank? returns false (Randy Schmidt)
  * fix typo in request specs (Paco Guzman)

### 2.4.1 / 2011-01-03

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.4.0...v2.4.1)

* Bug fixes
  * fixed bug caused by including some Rails modules before RSpec's
    RailsExampleGroup

### 2.4.0 / 2011-01-02

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.3.1...v2.4.0)

* Enhancements
  * include ApplicationHelper in helper object in helper specs
  * include request spec extensions in files in spec/integration
  * include controller spec extensions in groups that use :type => :controller
    * same for :model, :view, :helper, :mailer, :request, :routing

* Bug fixes
  * restore global config.render_views so you only need to say it once
  * support overriding render_views in nested groups
  * matchers that delegate to Rails' assertions capture
    ActiveSupport::TestCase::Assertion (so they work properly now with
    should_not in Ruby 1.8.7 and 1.9.1)

* Deprecations
  * include_self_when_dir_matches

### 2.3.1 / 2010-12-16

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.3.0...v2.3.1)

* Bug fixes
  * respond_to? correctly handles 2 args
  * scaffold generator no longer fails on autotest directory

### 2.3.0 / 2010-12-12

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.2.1...v2.3.0)

* Changes
  * Generator no longer generates autotest/autodiscover.rb, as it is no longer
    needed (as of rspec-core-2.3.0)

### 2.2.1 / 2010-12-01

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.2.0...v2.2.1)

* Bug fixes
  * Depend on railties, activesupport, and actionpack instead of rails (Piotr
    Solnica)
  * Got webrat integration working properly across different types of specs

* Deprecations
  * --webrat-matchers flag for generators is deprecated. use --webrat instead.

### 2.2.0 / 2010-11-28

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.1.0...v2.2.0)

* Enhancements
  * Added stub_template in view specs

* Bug fixes
  * Properly include helpers in views (Jonathan del Strother)
  * Fix bug in which method missing led to a stack overflow
  * Fix stack overflow in request specs with open_session
  * Fix stack overflow in any spec when method_missing was invoked
  * Add gem dependency on rails ~> 3.0.0 (ensures bundler won't install
    rspec-rails-2 with rails-2 apps).

### 2.1.0 / 2010-11-07

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.0.1...v2.1.0)

* Enhancements
  * Move errors_on to ActiveModel to support other AM-compliant ORMs

* Bug fixes
  * Check for presence of ActiveRecord instead of checking Rails config
    (gets rspec out of the way of multiple ORMs in the same app)

### 2.0.1 / 2010-10-15

[full changelog](http://github.com/rspec/rspec-rails/compare/v2.0.0...v2.0.1)

* Enhancements
  * Add option to not generate request spec (--skip-request-specs)

* Bug fixes
  * Updated the mock_[model] method generated in controller specs so it adds
    any stubs submitted each time it is called.
  * Fixed bug where view assigns weren't making it to the view in view specs in Rails-3.0.1.
    (Emanuele Vicentini)

### 2.0.0 / 2010-10-10

[full changelog](https://github.com/rspec/rspec-rails/compare/ea6bdef...v2.0.0)

* Enhancements
  * ControllerExampleGroup uses controller as the implicit subject by default (Paul Rosania)
  * autotest mapping improvements (Andreas Neuhaus)
  * more cucumber features (Justin Ko)
  * clean up spec helper (Andre Arko)
  * add assign(name, value) to helper specs (Justin Ko)
  * stub_model supports primary keys other than id (Justin Ko)
  * support choice between Webrat/Capybara (Justin Ko)
  * support specs for 'abstract' subclasses of ActionController::Base (Mike Gehard)
  * be_a_new matcher supports args (Justin Ko)

* Bug fixes
  * support T::U components in mailer and request specs (Brasten Sager)
