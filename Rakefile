#!/usr/bin/env ruby
# -*- ruby -*-

require 'rake/clean'

SRC_DIR      = 'src'
PROB_DIR     = 'koans'

SRC_FILES = FileList["#{SRC_DIR}/*"]
KOAN_FILES = SRC_FILES.pathmap("#{PROB_DIR}/%f")

task :default => :walk_the_path

task :walk_the_path do
  `open koans/jskoans.htm`
end

directory PROB_DIR

desc "Generate the Koans from the source files from scratch."
task :regen => [:clobber_koans, :gen]

desc "Generate the Koans from the changed source files."
task :gen => KOAN_FILES + [PROB_DIR]
task :clobber_koans do
  rm_r PROB_DIR
end

SRC_FILES.each do |koan_src|
  file koan_src.pathmap("#{PROB_DIR}/%f") => [PROB_DIR, koan_src] do |t|
    cp koan_src, t.name
  end
end
