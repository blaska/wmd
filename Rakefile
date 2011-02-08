##
## JS & CSS Compression/Compilation/Minification Tasks
##

# Paths to Google Closure & YUI Compressor
CLOSURE_COMPILER_PATH = '~/utilities/closure-compiler/compiler.jar'
YUI_COMPRESSOR_PATH = '~/utilities/yuicompressor/yuicompressor-2.4.2.jar'
# JS & CSS Source Code
JS_SOURCE_FILES = ['src/jquery.wmd.plugin.js', 'src/showdown.js', 'src/wmd.js'].map { |f| "--js=#{f}" }.join(" ")
CSS_SOURCE_FILE = 'src/wmd.css'
# JS & CSS Output files
JS_OUTPUT_FILE = 'minified/jquery.wmd.min.js'
CSS_OUTPUT_FILE = 'minified/wmd.min.css'

desc "Compile Javascript with Google Closure Compiler & minify CSS with YUI Compressor"
task :compile do
  # Combine & compile JS
  `java -jar #{CLOSURE_COMPILER_PATH} #{JS_SOURCE_FILES} --js_output_file=#{JS_OUTPUT_FILE}`
  
  # Minify CSS
  `java -jar #{YUI_COMPRESSOR_PATH} --type css --line-break 0 #{CSS_SOURCE_FILE} -o #{CSS_OUTPUT_FILE}`
  
  # Copy Images
  `cp -f src/images/wmd-buttons.png minified/images/wmd-buttons.png`
end