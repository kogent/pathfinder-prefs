require 'rake'
require 'yaml'
require 'plist'

path_finder_plist = "~/Library/Preferences/com.cocoatech.PathFinder.plist"
tempfile = "pf.plist"
plist_cmd = "/usr/bin/plutil"

task :default => [:install_iterm_prefs]

desc "Default: install iTerm preferences into PathFinder"
task :install_iterm_prefs do
  Rake::Task["dump_plist"].execute
  plist = Plist::parse_xml(File.read(tempfile))
  custom_settings = YAML.load_file "iterm.yaml"
  plist = plist.merge custom_settings
  plist.save_plist tempfile
  system "#{plist_cmd} -convert binary1 #{tempfile} -o #{path_finder_plist}"
  File.unlink tempfile
end

task :remove_preferences_file do
  system "rm -f #{path_finder_plist}"
end

task :dump_plist do
  system "#{plist_cmd} -convert xml1 #{path_finder_plist} -o #{tempfile}"
end