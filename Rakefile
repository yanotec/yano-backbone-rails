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

  desc "Update Backbone marionette assets and dependencies"
  task :marionette => %w(marionette:clear marionette:babysitter marionette:radio marionette:adapters) do
    Dir.chdir ASSETS_PATH do
      version = Yano::Backbone::Rails::MARIONETTE_VERSION

      puts "Downloading marionette.js"
      puts "curl -o ./javascripts/marionette/backbone.marionette.js https://raw.githubusercontent.com/marionettejs/backbone.marionette/v#{version}/lib/core/backbone.marionette.js"
      puts `curl -o ./javascripts/marionette/backbone.marionette.js https://raw.githubusercontent.com/marionettejs/backbone.marionette/v#{version}/lib/core/backbone.marionette.js`

      puts "Downloading marionette.min.js"
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

  namespace :marionette do
    task :clear do
      puts "Cleaning temp folder"
      ["rm -rf ", "mkdir -p "].each do |cmd|
        puts "#{cmd} ./javascripts/marionette"
        puts `#{cmd} ./javascripts/marionette`
      end
    end

    task :babysitter do
      Dir.chdir ASSETS_PATH do
        version = Yano::Backbone::Rails::BABYSITTER_VERSION

        puts "Downloading babysitter.js"
        puts "curl -o ./javascripts/marionette/backbone.babysitter.js https://raw.githubusercontent.com/marionettejs/backbone.babysitter/v#{version}/lib/backbone.babysitter.js"
        puts `curl -o ./javascripts/marionette/backbone.babysitter.js https://raw.githubusercontent.com/marionettejs/backbone.babysitter/v#{version}/lib/backbone.babysitter.js`

        puts "Downloading babysitter.min.js"
        puts "curl -o ./javascripts/marionette/backbone.babysitter.min.js https://raw.githubusercontent.com/marionettejs/backbone.babysitter/v#{version}/lib/backbone.babysitteri.min.js"
        puts `curl -o ./javascripts/marionette/backbone.babysitter.min.js https://raw.githubusercontent.com/marionettejs/backbone.babysitter/v#{version}/lib/backbone.babysitter.min.js`
        File.open('./javascripts/marionette/backbone.babysitter.min.js', 'r') do |file|
          File.open("./javascripts/marionette/backbone.babysitter.min.js.erb", 'w') do |new_file|
            while (line = file.gets)
              if line =~ /sourceMappingURL/
                line = line.gsub("backbone.babysitter.min.js.map", "<%= asset_path 'backbone.babysitter.min.js.map' %>")
              end

              new_file.puts line
            end
          end
        end
        puts "rm -f ./javascripts/marionette/backbone.babysitter.min.js"
        puts `rm -f ./javascripts/marionette/backbone.babysitter.min.js`

        puts "Downloading babysitter.min.map"
        puts "mkdir -p ./source_maps"
        puts `mkdir -p ./source_maps`
        puts "curl -o ./source_maps/backbone.babysitter.min.js.map https://raw.githubusercontent.com/marionettejs/backbone.babysitter/v#{version}/lib/backbone.babysitter.min.js.map"
        puts `curl -o ./source_maps/backbone.babysitter.min.js.map https://raw.githubusercontent.com/marionettejs/backbone.babysitter/v#{version}/lib/backbone.babysitter.min.js.map`
      end
    end

    task :radio do
      Dir.chdir ASSETS_PATH do
        version = Yano::Backbone::Rails::RADIO_VERSION

        ["", ".min"].each do |type|
          filename = "backbone.radio#{type}.js"

          puts "Downloading #{filename}"
          puts "curl -o ./javascripts/marionette/#{filename} https://raw.githubusercontent.com/marionettejs/backbone.radio/v#{version}/build/#{filename}"
          puts `curl -o ./javascripts/marionette/#{filename} https://raw.githubusercontent.com/marionettejs/backbone.radio/v#{version}/build/#{filename}`
          File.open("./javascripts/marionette/#{filename}", 'r') do |file|
            File.open("./javascripts/marionette/#{filename}.erb", 'w') do |new_file|
              while (line = file.gets)
                if line =~ /sourceMappingURL/
                  line = line.gsub("#{filename}.map", "<%= asset_path '#{filename}.map' %>")
                  line = line.gsub("./", "")
                end

                new_file.puts line
              end
            end
          end
          puts "rm -f ./javascripts/marionette/#{filename}"
          puts `rm -f ./javascripts/marionette/#{filename}`

          puts "Downloading #{filename}.map"
          puts "mkdir -p ./source_maps"
          puts `mkdir -p ./source_maps`
          puts "curl -o ./source_maps/#{filename}.map https://raw.githubusercontent.com/marionettejs/backbone.babysitter/v#{version}/lib/#{filename}.map"
          puts `curl -o ./source_maps/#{filename}.map https://raw.githubusercontent.com/marionettejs/backbone.babysitter/v#{version}/lib/#{filename}.map`
        end
      end
    end

    task :adapters do
      Dir.chdir ASSETS_PATH do
        puts "Downloading backbone.radio.adapter.js"
        puts "curl -o ./javascripts/marionette/backbone.radio.adapter.js https://gist.githubusercontent.com/jmeas/7992474cdb1c5672d88b/raw/92b9be3a72571bd5761d88179efb0e9b1e40a245/radio.shim.js"
        puts `curl -o ./javascripts/marionette/backbone.radio.adapter.js https://gist.githubusercontent.com/jmeas/7992474cdb1c5672d88b/raw/92b9be3a72571bd5761d88179efb0e9b1e40a245/radio.shim.js`

        puts "Downloading backbone.handlebars.adapter.js"
        puts "curl -o ./javascripts/marionette/backbone.handlebars.adapter.js https://gist.githubusercontent.com/jonathanccalixto/a3223950577e9de3d3e00acc1f3ee5f2/raw/ea88cccbe3bcbb8c3a0bdb17a6683e4d58a353c4/backbone.handlebars.adapter.js"
        puts `curl -o ./javascripts/marionette/backbone.handlebars.adapter.js https://gist.githubusercontent.com/jonathanccalixto/a3223950577e9de3d3e00acc1f3ee5f2/raw/ea88cccbe3bcbb8c3a0bdb17a6683e4d58a353c4/backbone.handlebars.adapter.js`
      end
    end
  end
end
