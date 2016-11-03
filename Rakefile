# encoding: utf-8
#!/usr/bin/env rake
require "rubygems"
require "bundler/setup"
require "bundler/gem_tasks"
require "rake"

begin
  require "wwtd/tasks"
  require "rspec/core/rake_task"
  RSpec::Core::RakeTask.new(:spec)
  task :default => :spec
rescue LoadError
  warn "Failed to load rspec or wwtd"
end

require "reek/rake/task"
Reek::Rake::Task.new do |t|
  t.fail_on_error = true
  t.verbose = false
  t.source_files = "lib/**/*.rb"
end

require "roodi"
require "roodi_task"
RoodiTask.new do |t|
  t.verbose = false
end

require File.expand_path("../lib/sanitize_email/version", __FILE__)
require "rdoc"
require "rdoc/task"
RDoc::Task.new do |rdoc|
  rdoc.rdoc_dir = "rdoc"
  rdoc.title    = "SanitizeEmail #{SanitizeEmail::VERSION}"
  rdoc.options << "--line-numbers"
  rdoc.rdoc_files.include("README*")
  rdoc.rdoc_files.include("lib/**/*.rb")
end

Bundler::GemHelper.install_tasks
