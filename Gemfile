# Basic gemfile for local testing of github-pages repos on Windows

source 'https://rubygems.org'
gem "github-pages", '~> 231', group: :jekyll_plugins

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Fix listen behavior on Windows
gem 'wdm', '~> 0.1.1', :install_if => Gem.win_platform?

# Removed from the standard library in Ruby 3.X so must add manually
gem "webrick", "~> 1.7"
