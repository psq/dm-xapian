require 'rubygems'
require 'rake/gempackagetask'
require 'rubygems/specification'
require 'date'
require 'merb-core/version'
require 'merb-core/tasks/merb_rake_helper'

NAME = "dm-xapian"
GEM_VERSION = "0.5"
AUTHOR = "Joshaven Potter, Pascal Belloncle"
EMAIL = "yourtech@gmail.com, psq@nanorails.com"
HOMEPAGE = "http://github.com/psq/dm-xapian"
SUMMARY = "Merb plugin that provides use of the Ruby Xapian search engine library"

spec = Gem::Specification.new do |s|
  s.rubyforge_project = 'merb'
  s.name = NAME
  s.version = GEM_VERSION
  s.platform = Gem::Platform::RUBY
  s.has_rdoc = true
  s.extra_rdoc_files = ["README.txt", "LICENSE", 'TODO', 'SETUP.txt', 'CHANGES.txt']
  s.summary = SUMMARY
  s.description = s.summary
  s.author = AUTHOR
  s.email = EMAIL
  s.homepage = HOMEPAGE
  s.add_dependency('merb', '>= 0.9.7')
  s.require_path = 'lib'
  s.files = %w(LICENSE README.txt Rakefile TODO CHANGES.txt SETUP.txt) + Dir.glob("{lib,spec}/**/*")
  
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end

desc "install the plugin locally"
task :install => [:package] do
  Merb::RakeHelper.install(NAME, :version => GEM_VERSION)
  # sudo "gem install #{install_home} pkg/#{NAME}-#{GEM_VERSION} --no-update-sources"
end

desc "create a gemspec file"
task :make_spec do
  File.open("#{NAME}.gemspec", "w") do |file|
    file.puts spec.to_ruby
  end
end

namespace :jruby do

  desc "Run :package and install the resulting .gem with jruby"
  task :install => :package do
    sudo "jruby -S gem install #{install_home} pkg/#{NAME}-#{GEM_VERSION}.gem --no-rdoc --no-ri"
  end

end
