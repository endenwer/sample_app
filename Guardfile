guard 'livereload', notify: true do
  watch(%r{app/views/.+\.(erb|haml|slim)$})
  watch(%r{app/helpers/.+\.rb})
  watch(%r{public/.+\.(css|js|html)})
  watch(%r{config/locales/.+\.yml})
  # Rails Assets Pipeline
  watch(%r{(app|vendor)(/assets/\w+/(.+\.(css|js|html|png|jpg))).*}) { |m| "/assets/#{m[3]}" }
end


guard :bundler do
  watch('Gemfile')
end


guard 'rails', zeus: true do
  watch('Gemfile.lock')
  watch(%r{^(config|lib)/.*})
end


guard :rspec, cmd: 'zeus rspec' do
  watch(%r{^spec/.+_spec\.rb})
  watch(%r{^lib/(.+)\.rb})                            { |m| "spec/lib/#{m[1]}_spec.rb" }
  watch('spec/spec_helper.rb')                        { "spec" }

  #run the model specs
  watch(%r{^app/views/(.+)/})                         { |_m| 'spec/requests/' }

  #run the controller specs
  watch(%r{^app/controllers/(.+)_(controller)\.rb})   { |m| ["spec/routing/#{m[1]}_routing_spec.rb", "spec/#{m[2]}s/#{m[1]}_#{m[2]}_spec.rb", "spec/acceptance/#{m[1]}_spec.rb"] }

  # Rails example
  watch('config/routes.rb')                           { "spec/routing" }
  watch('app/controllers/application_controller.rb')  { "spec/controllers" }
  watch(%r{^app/(.+)\.rb})                            { |m| "spec/#{m[1]}_spec.rb" }
  watch(%r{^lib/(.+)\.rb})                            { |m| "spec/lib/#{m[1]}_spec.rb" }
end


guard 'migrate' do
  watch(%r{^db/migrate/(\d+).+\.rb})
  watch('db/seeds.rb')
end
