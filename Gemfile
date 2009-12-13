disable_system_gems
bin_path 'gbin'

only :release do
  gem 'ruby-hmac', '>= 0.3.1'
end

only :development do
  gem 'rake'
  gem 'rack'
  gem 'bundler'
  gem 'test-unit',    '>=2.0.5'
  gem 'actionpack',    '=2.2.2', :require_as => %w(action_pack)
end
