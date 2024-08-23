source "https://rubygems.org"

# GitHub Pages gem, which includes Jekyll and necessary plugins
gem "github-pages", group: :jekyll_plugins

# Additional Jekyll plugins
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
end

# tzinfo-data gem for Windows and JRuby
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Update wdm to the version installed on your system
gem "wdm", "~> 0.2.0", platforms: [:mingw, :x64_mingw, :mswin]

# Lock http_parser.rb version on JRuby
gem "http_parser.rb", "~> 0.6.0", platforms: [:jruby]


gem "jekyll-paginate"
gem 'faraday-retry'
