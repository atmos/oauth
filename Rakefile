Bundler.require_env(:development)
require 'rake'
require 'rake/gempackagetask'
require 'rake/clean'
require 'fileutils'
require 'bundler'

$LOAD_PATH << File.dirname(__FILE__) + '/lib'
require 'oauth/version'

task :default => [:test]
Dir['tasks/**/*.rake'].each { |t| load t }

spec = Gem::Specification.new do |s|
  s.name             = "oauth"
  s.version          = OAuth::VERSION
  s.authors          = [ 'Pelle Braendgaard', 'Blaine Cook', 'Larry Halff', 'Jesse Clark', 'Jon Crosby', 'Seth Fitzsimmons' ]
  s.email            = "oauth-ruby@googlegroups.com"
  s.homepage         = "http://oauth.rubyforge.org"
  s.description      = s.summary = "OAuth Core Ruby implementation"

  s.platform         = Gem::Platform::RUBY
  s.has_rdoc         = true
  s.extra_rdoc_files = ["README.rdoc"]

  manifest = Bundler::Environment.load(File.dirname(__FILE__) + '/Gemfile')
  manifest.dependencies.each do |d|
    if d.only && d.only.include?('release')
      s.add_dependency(d.name, d.version)
    end
  end

  s.require_path = 'lib'
  s.files = %w(License.txt History.txt README.rdoc Rakefile TODO) + Dir.glob("{lib,test,examples}/**/*")

  s.bindir = "bin"
  s.executables = %w( oauth )
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end

require 'rake/testtask'
Rake::TestTask.new do |t|
  t.libs << "test"
  t.test_files = FileList['test/test*.rb']
  t.verbose = true
end
