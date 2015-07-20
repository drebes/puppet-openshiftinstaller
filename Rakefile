require 'rubygems'
require 'puppetlabs_spec_helper/rake_tasks'

begin
    require 'puppet_blacksmith/rake_tasks'
rescue LoadError
end

exclude_paths = [
    "pkg/**/*",
      "vendor/**/*",
        "spec/**/*",
]

PuppetLint.configuration.relative = true
PuppetLint.configuration.fail_on_warnings
PuppetLint.configuration.ignore_paths = exclude_paths
PuppetLint.configuration.log_format = "%{path}:%{linenumber}:%{check}:%{KIND}:%{message}"
PuppetLint.configuration.send('relative')
PuppetLint.configuration.send('disable_80chars')
PuppetLint.configuration.send('disable_class_inherits_from_params_class')
PuppetLint.configuration.send('disable_arrow_alignment')
PuppetSyntax.exclude_paths = exclude_paths

desc "Run acceptance tests"
RSpec::Core::RakeTask.new(:acceptance) do |t|
    t.pattern = 'spec/acceptance'
end

desc "Run syntax, lint, and spec tests."
task :test => [
  :syntax,
  :lint,
  :spec,
]

