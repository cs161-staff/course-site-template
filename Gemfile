source 'https://rubygems.org'
gem 'jekyll', '~> 4'

gem 'faraday-retry', '~> 2.2'
gem 'kramdown-parser-gfm'
gem 'csv'
gem 'bigdecimal'
gem 'logger'

group :jekyll_plugins do
  gem 'jekyll-github-metadata', '~> 2.16'
#   gem 'jekyll-jupyter-notebook' # Enable if you want to use Jupyter notebooks
  gem 'jekyll-redirect-from'
  gem 'jekyll-sitemap'
  gem 'jemoji'
  gem 'just-the-docs', '~> 0.10.1'
  gem 'jekyll-relative-links'
end

# These tools are use for running tests.
group :development, :test do
  gem 'axe-core-capybara'
  gem 'axe-core-rspec'
  gem 'capybara'
  gem 'capybara-screenshot'
  gem 'rack'
  gem 'rackup'
  gem 'rspec'
  gem 'selenium-webdriver'
  gem "webrick", "~> 1.7"
end

group :development, :rubocop do
  gem 'rubocop', require: false
  gem 'rubocop-capybara', require: false
  gem 'rubocop-rspec', require: false
end
