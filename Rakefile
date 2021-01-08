abort("Please run this using `bundle exec rake`") unless ENV["BUNDLE_BIN_PATH"]
require "html-proofer"

desc "Build website with jekyll and test with html-proofer"
task :test do
  sh "bundle exec jekyll build"
  options = {
    :allow_hash_href => true,
    :check_html => true,
    :empty_alt_ignore => true,
    :http_status_ignore => [0,400,503,999],
    :url_ignore => ["/archive/v3/irc/"],
    :cache => {
      :timeframe => "6w"
    }
  }
  HTMLProofer.check_directory("./_site/", options).run
end

task :default => [:test]
