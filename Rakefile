require "bundler/gem_tasks"
require "rake/testtask"

task default: :test
Rake::TestTask.new do |t|
  t.libs << "test"
  t.pattern = "test/**/*_test.rb"
end

def download_file(file)
  require "open-uri"

  url = "https://github.com/ankane/ml-builds/releases/download/cmfrec-2.4.1/#{file}"
  puts "Downloading #{file}..."
  dest = "vendor/#{file}"
  File.binwrite(dest, URI.open(url).read)
  puts "Saved #{dest}"
end

namespace :vendor do
  task :linux do
    download_file("libcmfrec.so")
  end

  task :mac do
    download_file("libcmfrec.dylib")
    download_file("libcmfrec.arm64.dylib")
  end

  task :windows do
    # download_file("cmfrec.dll")
  end

  task all: [:linux, :mac, :windows]
end
