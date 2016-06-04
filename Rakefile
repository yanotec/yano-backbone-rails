require "bundler/gem_tasks"
task :default => :spec

# path to your application root.
GEM_ROOT = Pathname.new File.expand_path('../',  __FILE__)
ASSETS_PATH = Pathname.new File.expand_path('vendor/assets/',  GEM_ROOT)

desc "Update all assets"
task :update => %w(update:underscore update:backbone update:marionette)

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

  desc "Update backbone assets"
  task :backbone do
    version = Yano::Backbone::Rails::BACKBONE_VERSION

    Dir.chdir ASSETS_PATH do
      puts "Cleaning temp folder"
      ["rm -rf ", "mkdir -p "].each do |cmd|
        puts "#{cmd} ./javascripts/backbone"
        puts `#{cmd} ./javascripts/backbone`
      end

      puts "Downloading backbone.js"
      puts "curl -o ./javascripts/backbone/backbone.js https://raw.githubusercontent.com/jashkenas/backbone/#{version}/backbone.js"
      puts `curl -o ./javascripts/backbone/backbone.js https://raw.githubusercontent.com/jashkenas/backbone/#{version}/backbone.js`

      puts "Downloading backbone.min.js"
      puts "curl -o ./javascripts/backbone/backbone.min.js https://raw.githubusercontent.com/jashkenas/backbone/#{version}/backbone-min.js"
      puts `curl -o ./javascripts/backbone/backbone.min.js https://raw.githubusercontent.com/jashkenas/backbone/#{version}/backbone-min.js`
      File.open('./javascripts/backbone/backbone.min.js', 'r') do |file|
        File.open("./javascripts/backbone/backbone.min.js.erb", 'w') do |new_file|
          while (line = file.gets)
            if line =~ /sourceMappingURL/
              line = line.gsub("backbone-min.map", "<%= asset_path 'backbone.min.map' %>")
            end

            new_file.puts line
          end
        end
      end
      puts "rm -f ./javascripts/backbone/backbone.min.js"
      puts `rm -f ./javascripts/backbone/backbone.min.js`

      puts "Downloading backbone.min.map"
      puts "mkdir -p ./source_maps"
      puts `mkdir -p ./source_maps`
      puts "curl -o ./source_maps/backbone.min.map https://raw.githubusercontent.com/jashkenas/backbone/#{version}/backbone-min.map"
      puts `curl -o ./source_maps/backbone.min.map https://raw.githubusercontent.com/jashkenas/backbone/#{version}/backbone-min.map`
    end

    puts "\e[32mDone!\e[0m"
  end

  desc "Update Backbone marionette assets"
  task :marionette do
    version = Yano::Backbone::Rails::MARIONETTE_VERSION

    Dir.chdir ASSETS_PATH do
      puts "Cleaning temp folder"
      ["rm -rf ", "mkdir -p "].each do |cmd|
        puts "#{cmd} ./javascripts/marionette"
        puts `#{cmd} ./javascripts/marionette`
      end

      puts "Downloading backbone.js"
      puts "curl -o ./javascripts/marionette/backbone.marionette.js https://raw.githubusercontent.com/marionettejs/backbone.marionette/v#{version}/lib/core/backbone.marionette.js"
      puts `curl -o ./javascripts/marionette/backbone.marionette.js https://raw.githubusercontent.com/marionettejs/backbone.marionette/v#{version}/lib/core/backbone.marionette.js`

      puts "Downloading backbone.min.js"
      puts "curl -o ./javascripts/marionette/backbone.marionette.min.js https://raw.githubusercontent.com/marionettejs/backbone.marionette/v#{version}/lib/core/backbone.marionette.min.js"
      puts `curl -o ./javascripts/marionette/backbone.marionette.min.js https://raw.githubusercontent.com/marionettejs/backbone.marionette/v#{version}/lib/core/backbone.marionette.min.js`
      File.open('./javascripts/marionette/backbone.marionette.min.js', 'r') do |file|
        File.open("./javascripts/marionette/backbone.marionette.min.js.erb", 'w') do |new_file|
          while (line = file.gets)
            if line =~ /sourceMappingURL/
              line = line.gsub("backbone.marionette.min.js.map", "<%= asset_path 'backbone.marionette.min.js.map' %>")
            end

            new_file.puts line
          end
        end
      end
      puts "rm -f ./javascripts/marionette/backbone.marionette.min.js"
      puts `rm -f ./javascripts/marionette/backbone.marionette.min.js`

      puts "Downloading backbone.min.map"
      puts "mkdir -p ./source_maps"
      puts `mkdir -p ./source_maps`
      puts "curl -o ./source_maps/backbone.marionette.min.js.map https://raw.githubusercontent.com/marionettejs/backbone.marionette/v#{version}/lib/core/backbone.marionette.min.js.map"
      puts `curl -o ./source_maps/backbone.marionette.min.js.map https://raw.githubusercontent.com/marionettejs/backbone.marionette/v#{version}/lib/core/backbone.marionette.min.js.map`
    end

    puts "\e[32mDone!\e[0m"
  end
end
