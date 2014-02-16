#!/usr/bin/env rake
require 'rake/clean'

raise "Missing .article-name file" unless File.exist? '.article-name'
ARTICLE=File.open('.article-name').readlines[0].chomp

CLEAN.include([ '*.html', '*.pdf' ])

desc "Show current theme (conferene name)"
task :show do
  puts ARTICLE
end

desc "Make all files"
task :default => [ "html" ]

desc "Generate single html file"
task :html => [ "#{ARTICLE}.html" ]

desc "Generate single html file"
file "#{ARTICLE}.html" => [ "#{ARTICLE}.txt" ] do
    puts "I start to make #{ARTICLE}.html"
    sh "asciidoc #{ARTICLE}.txt"
end

desc "Generate single pdf file"
task :pdf => [ "#{ARTICLE}.pdf" ]

desc "Generate single pdf file"
file "#{ARTICLE}.pdf" => [ "#{ARTICLE}.txt" ] do
    puts "I start to make #{ARTICLE}.pdf"
    sh "a2x -f pdf --fop --verbose --no-xmllint #{ARTICLE}.txt"
end
