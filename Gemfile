# frozen_string_literal: true

source "https://rubygems.org"

# Use Jekyll 4.x for better compatibility
gem "jekyll", "~> 4.3"
gem "kramdown", "~> 2.3.0"
gem "kramdown-parser-gfm", "~> 1.1"

# For GitHub Pages compatibility
group :jekyll_plugins do
  gem "jekyll-paginate", "~> 1.1"
  gem "jekyll-sitemap", "~> 1.4"
end

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Lock `http_parser.rb` gem to `v0.6.x` on JRuby builds since newer versions of the gem
# do not have a Java counterpart.
# See https://github.com/eventmachine/eventmachine/issues/343
# If you have any issues, please report them to https://github.com/eventmachine/eventmachine/issues/new
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]

