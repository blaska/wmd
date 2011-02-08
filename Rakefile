require 'rubygems'
require File.expand_path("utilities/cssmin")

JS_SOURCE_FILES  = ['src/jquery.wmd.plugin.js', 'src/showdown.js', 'src/wmd.js'].map { |f| "--js=#{f}" }.join(" ")
CSS_SOURCE_FILE  = ['src/wmd.css'].map.join(" ")
COMPILER_PATH    = '~/utilities/closure-compiler/compiler.jar'
JS_OUTPUT_FILE   = 'minified/jquery.wmd.min.js'
CSS_OUTPUT_FILE  = 'minified/wmd.css'

desc "Compile Javascript with Google Closure Compiler & move JS/CSS/Image files to minified directory"
task :compile do
  # Combine & compile JS
  `java -jar #{COMPILER_PATH} #{JS_SOURCE_FILES} --js_output_file=#{JS_OUTPUT_FILE}`
  
  # Minify CSS
  File.open(CSS_SOURCE_FILE, 'r') { |input| File.open(CSS_OUTPUT_FILE, 'w') { |output| output.write(CSSMin.minify(input)) }}
  
  # Copy Images
  `cp -f src/images/wmd-buttons.png minified/images/wmd-buttons.png`
end