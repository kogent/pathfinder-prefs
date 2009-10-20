require 'rake'
require 'yaml'
require 'plist'

task :default => [:install_iterm_prefs]

desc "Default: install iTerm preferences into PathFinder"
task :install_iterm_prefs do
  tempfile = "#{ENV['TMPDIR']}/PF.plist"
  tempfile = "PF.plist"
  path_finder_plist = "$HOME/Library/Preferences/com.cocoatech.PathFinder.plist"
  system "/usr/bin/plutil -convert xml1 #{path_finder_plist} -o #{tempfile}"
  plist = Plist::parse_xml(File.read(tempfile))
  custom_settings = YAML.load_file "iterm.yaml"
  plist = plist.merge custom_settings
  plist.save_plist tempfile
  system "/usr/bin/plutil -convert binary1 #{tempfile} -o #{path_finder_plist}"
  File.unlink tempfile
end

