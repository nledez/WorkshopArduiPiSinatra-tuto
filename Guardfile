guard :shell do
  watch(/RubySinatra.txt/) {|m| `asciidoc RubySinatra.txt` }
end

guard 'livereload' do
  watch(%r{.+\.html$})
end
