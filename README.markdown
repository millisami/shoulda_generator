# shoulda generators

One night at a Boston Ruby hackfest, I finally got sick of using the Rails default generators, and have to hack them to meet my needs and tastes. This includes:

 * [shoulda](http://thoughtbot.com/projects/shoulda)
 * [factory_girl](http://github.com/thoughtbot/factory_girl)
 * [haml](http://haml.hamptoncatlin.com/)
 * [blueprint](http://code.google.com/p/blueprintcss/)


The next morning, I was struck awake at 5am with the inspiration to start implementing it.

## what you get

### shoulda\_model

 * works the same as the 'model' generator
 * a new model
 * a migration for the model
 * a factory using [factory_girl](http://github.com/thoughtbot/factory_girl)
 * a [shoulda](http://thoughtbot.com/projects/shoulda) unit test with a few simple 'should's

#### Prereqs:

 * [shoulda](http://thoughtbot.com/projects/shoulda) installed as a plugin
 * [factory_girl](http://github.com/thoughtbot/factory_girl) gem installed

In `test/test_helper.rb`, include this:

    require 'factory_girl'
    Dir[File.join(RAILS_ROOT, 'test', 'factories', '*')].each do |file|
      require file
    end

### shoulda\_haml\_scaffold

 * everything included in shoulda_model
 * a controller (sans unnecessary comments)
 * templates built written in [haml](http://haml.hamptoncatlin.com/)
 * a layout written in [haml](http://haml.hamptoncatlin.com/) and styled with [blueprint](http://code.google.com/p/blueprintcss/)
 * a helper
 * a shoulda functional test which uses the factory_girl factory

Prereqs:

 * [shoulda](http://thoughtbot.com/projects/shoulda) installed as a plugin
 * [factory_girl](http://github.com/thoughtbot/factory_girl) gem installed
 * [haml](http://haml.hamptoncatlin.com/) gem installed on the system, and the project has been hamlified using  `haml --rails` on the project
 * the code snippet above for `test/test_helper.rb`

## getting it

You can install it as a plugin for the time being. I plan on having a gem soon enough.

With Rails 2.1, you can do:

    $ script/plugin install git://github.com/technicalpickles/shoulda-generators.git

... or better yet, use piston 1.9.x...

    $ piston install git://github.com/technicalpickles/shoulda-generators.git vendor/plugins/shoulda-generators

## using it

Usage is the same as the default Rails generators.

    $ script/generate shoulda_model post title:string body:text published:boolean 
    $ script/generate shoulda_scaffold post title:string body:text published:boolean 

## developing it

Make a checkout somewhere:

    $ git clone git://github.com/technicalpickles/shoulda-generators.git

Add symlinks so that Rails will pickup the generators from your checkout:

    $ mkdir -p ~/.rails/generators
    $ ln -s shoulda-generators/*_generator ~/.rails/generators

Send pull requests to me, and I'll take a look at them.