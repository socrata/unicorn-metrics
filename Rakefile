require 'bundler/gem_tasks'
require 'rake/testtask'

Rake::TestTask.new do |t|
    t.libs << 'test'
    t.verbose = true
end

desc "Run tests"
task :default => :test

namespace :gem do
  desc 'Build Gem'
  task :build do
    puts("Building unicorn_metrics-#{UnicornMetrics::VERSION}.gem")
    puts `gem build unicorn_metrics.gemspec`
  end

  desc 'Publish Gem'
  task :publish do
    puts("Publishing unicorn_metrics-#{UnicornMetrics::VERSION}.gem")
    # NOTE: the --host path cannot end in a slash. If it does you will get a mysterious 405 error
    puts `gem push unicorn_metrics-#{UnicornMetrics::VERSION}.gem --host https://socrata.artifactoryonline.com/socrata/api/gems/rubygems-virtual`
  end
end

task :gem => ['gem:build', 'gem:publish']
