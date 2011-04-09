require 'rubygems'

# This requires you to have PrinceXML installed
# The rake task regenerates
# the site with Jekyll, then builds a new manual.pdf
# Delete the old manual.pdf first before running the task
desc "Generate printed manual as manual.pdf"
file 'manual.pdf' => '_site' do |task|
  sh 'jekyll'
  pages = File.read('_site/printed.html').scan(/<li><a href=['"]([^'"]+)/).flatten.map { |f| "_site/#{f}" }
  sh 'prince', '--input=html', '--style=_site/css/printed-pdf.css', '--no-network', '--log=prince_errors.log', "--output=#{task.name}", '_site/printed.html', *pages
end
