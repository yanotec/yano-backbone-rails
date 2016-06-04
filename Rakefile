require "bundler/gem_tasks"
task :default => :spec

# path to your application root.
GEM_ROOT = Pathname.new File.expand_path('../',  __FILE__)
ASSETS_PATH = Pathname.new File.expand_path('vendor/assets/',  GEM_ROOT)

desc "Update all assets"
task :update => %w(update:underscore)

namespace :update do
  desc "Update underscore assets"
  task :underscore do
    version = Yano::Backbone::Rails::UNDERSCORE_VERSION

    Dir.chdir ASSETS_PATH do
      puts "Cleaning temp folder"
      ["rm -rf ", "mkdir -p "].each do |cmd|
        puts "#{cmd} ./javascripts/underscore"
        puts `#{cmd} ./javascripts/underscore`
      end

      puts "Downloading underscore.js"
      puts "curl -o ./javascripts/underscore/underscore.js https://raw.githubusercontent.com/jashkenas/underscore/#{version}/underscore.js"
      puts `curl -o ./javascripts/underscore/underscore.js https://raw.githubusercontent.com/jashkenas/underscore/#{version}/underscore.js`

      puts "Downloading underscore.min.js"
      puts "curl -o ./javascripts/underscore/underscore.min.js https://raw.githubusercontent.com/jashkenas/underscore/#{version}/underscore-min.js"
      puts `curl -o ./javascripts/underscore/underscore.min.js https://raw.githubusercontent.com/jashkenas/underscore/#{version}/underscore-min.js`
      File.open('./javascripts/underscore/underscore.min.js', 'r') do |file|
        File.open("./javascripts/underscore/underscore.min.js.erb", 'w') do |new_file|
          while (line = file.gets)
            if line =~ /sourceMappingURL/
              line = line.gsub("underscore-min.map", "<%= asset_path 'underscore.min.map' %>")
            end

            new_file.puts line
          end
        end
      end
      puts "rm -f ./javascripts/underscore/underscore.min.js"
      puts `rm -f ./javascripts/underscore/underscore.min.js`

      puts "Downloading underscore.min.map"
      puts "mkdir -p ./source_maps"
      puts `mkdir -p ./source_maps`
      puts "curl -o ./source_maps/underscore.min.map https://raw.githubusercontent.com/jashkenas/underscore/#{version}/underscore-min.map"
      puts `curl -o ./source_maps/underscore.min.map https://raw.githubusercontent.com/jashkenas/underscore/#{version}/underscore-min.map`
    end

    puts "\e[32mDone!\e[0m"
  end
end
