#!/usr/bin/env rake
require 'rake/clean'

raise "Missing .article-name file" unless File.exist? '.article-name'
ARTICLE=File.open('.article-name').readlines[0].chomp

CLEAN.include([ '*.html', '*.pdf', '*.xml' ])

desc "Show current theme (conferene name)"
task :show do
  puts ARTICLE
end

desc "Make all files"
task :default => [ "html" ]

desc "Generate single html file"
task :html => [ "#{ARTICLE}.html" ]

desc "Generate single html file"
file "#{ARTICLE}.html" => [ "README.adoc" ] do
    puts "I start to make #{ARTICLE}.html"
    sh "asciidoctor -d article README.adoc -o #{ARTICLE}.html"
end

desc "Generate single pdf file"
task :pdf => [ "#{ARTICLE}.pdf" ]

desc "Generate single pdf file"
file "#{ARTICLE}.pdf" => [ "README.adoc" ] do
    puts "I start to make #{ARTICLE}.pdf"
    sh "asciidoctor -b docbook5 -d article README.adoc -o #{ARTICLE}.xml && ../asciidoctor-fopub/fopub #{ARTICLE}.xml"
end
