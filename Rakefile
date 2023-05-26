#!/usr/bin/env ruby

require 'rake/testtask'
require 'rubygems'
require 'rake'
require 'haml'

task default: :compile

task :compile do
  FileList.new('./src/*.html.haml').each do |filename|
    if filename =~ /([^\/]+)\.haml$/
      File.open($1, 'w') do |f|
        file_content = File.read(filename)
        puts file_content
        f.write Haml::Engine.new(file_content).render
      end
    end
  end
end

task :clean do
  FileUtils.rm_r(Dir.glob("./*.html"), force: true)
end

task :test do 
  Rake::TestTask.new do |t|
    t.test_files = FileList['test/jenkins_sample_test.rb']
  end
end
