require 'rubygems' unless ENV['NO_RUBYGEMS']
%w[rake rake/clean fileutils newgem rubigen].each { |f| require f }
require File.dirname(__FILE__) + '/lib/authority-labs-client'

# Generate all the Rake tasks
# Run 'rake -T' to see list of generated tasks (from gem root directory)
$hoe = Hoe.new('authority-labs-client', AuthorityLabs::VERSION) do |p|
  p.developer('Cramer Development, Inc.', 'support@cramerdev.com')
  p.changes              = p.paragraphs_of("History.txt", 0..1).join("\n\n")
  p.rubyforge_name       = p.name
  p.extra_deps         = [
    ['rest-client','>= 1.0.3'],
    ['activesupport', '>= 2.3.2']
  ]
  p.extra_dev_deps = [
    ['newgem', ">= #{::Newgem::VERSION}"]
  ]
  
  p.clean_globs |= %w[**/.DS_Store tmp *.log]
  path = (p.rubyforge_name == p.name) ? p.rubyforge_name : "\#{p.rubyforge_name}/\#{p.name}"
  p.remote_rdoc_dir = File.join(path.gsub(/^#{p.rubyforge_name}\/?/,''), 'rdoc')
  p.rsync_args = '-av --delete --ignore-errors'
end

require 'newgem/tasks' # load /tasks/*.rake
Dir['tasks/**/*.rake'].each { |t| load t }
