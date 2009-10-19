require 'rake'

task :default => [:install_iterm_prefs]

desc "install iTerm preferences into PathFinder"
task :install_iterm_prefs do
  Dir['iTerm/*'].each do |file|
    system "cp -f #{file} /Applications/Path\\ Finder.app/Contents/Frameworks/iTerm.framework/Versions/A/Resources/"
  end
  system "rm -f $HOME/Library/Preferences/com.cocoatech.PathFinder.plist"
end

