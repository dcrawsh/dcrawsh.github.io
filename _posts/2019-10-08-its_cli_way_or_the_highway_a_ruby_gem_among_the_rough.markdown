---
layout: post
title:      " It's CLI way or the highway...a ruby gem among the rough!!!"
date:       2019-10-08 20:35:35 +0000
permalink:  its_cli_way_or_the_highway_a_ruby_gem_among_the_rough
---



 I began this journey with very little idea to what a Ruby gem was let alone how to create one.  In the following paragraphs I will describe to you in beautful detail how I rounded that corner and polished that Gem.
 https://upload.wikimedia.org/wikipedia/commons/7/73/Ruby_logo.svg
	
  First, using bundler in the terminal, I created a scaffold directory using the command `bundle gem portlandhike`. The scaffold directory provided by bundler created all the files and directories I needed to get started.
	 
Gemfile: specifies the source for all of my gem dependencies

Rakefile: Requires Bundler and adds the build, install and release

CODE_OF_CONDUCT.md: How you expect contributors to act, but not totally necessary.

LICENSE.txt: Includes the MIT license, which is typical of student developers

.gitignore:  This ignores anything in the pkg directory and anything with a .gem extension and the .bundle directory.

portlandhike.gemspec: This is the Gem Specification file where we provide information such as the name, and description.  Also this is where we specify the dependencies our gem needs to run.  Below are the two gems I needed to add dependencies for.

for parsing the text in the website:  spec.add_dependency "nokogiri"
for opening up a the website: spec.add_dependency 'cli-ui', '~> 1.3'


lib/portlandhike.rb: This is the main file to define our gem’s code. This is the file that will be required by Bundler when our gem is loaded. This file defines a module which we can use as a namespace for all our gem’s code. 
lib/portlandhike: This folder contains all the code for our gem. The lib/portlandhike.rb file is there for setting up our gem’s environment, and other .rb files go in here as well. 
lib/portlandhike/version.rb: Defines a Portlandhike module and in it, a VERSION constant. This file is loaded by the portlandhike.gemspec to specify a version for the gem specification. If I release a new version of the gem I would have to increment the version number.



