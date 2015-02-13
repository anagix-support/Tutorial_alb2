require 'erb'
require 'rubygems'
require 'ruby-debug'

task :default => [:html, :qthelp, :epub, :pdf] 

task :usage do
  puts "Usage: rake html, epub or pdf"
  puts "       rake public, denso ... to set target"
end

# ======================================================
selection = {
  'denso' => %w[alb_first_step verilog_a_sample alta_simulation alta_first_step schematic_creation schematic_creation_fujitsu65n ADEin_conversion],
  'public' => %w[alb_first_step verilog_a_sample alta_simulation alta_first_step schematic_creation ADEin_conversion],
  'alta_simulation' => %w[alta_simulation],
  'verilog_a_sample' => %w[verilog_a_sample],
  'ADE_conversion' => %w[ADEin_conversion],
}  

selection.each_pair{|tgt, sections|
  task tgt => 'index.erb' do |t|
    erb = ERB.new(File.read(t.prerequisites.first))
    contents = "   "+ sections.join("\n   ")
    File.open('index.rst', 'w'){|f| f.puts erb.result(binding)}
    puts File.read('index.rst')
  end
}
# ======================================================

Dir.glob('*.erb').each{|erb|
  file erb
}

task :dist do
  sh 'tar cvzfh Tutorials.tgz Tutorials install'
  sh 'cat install Tutorials.tgz > Tutorials.bin; rm Tutorials.tgz; chmod +x Tutorials.bin'
  puts '*** Tutorials.bin created ***'
end

targets = Rake.application.top_level_tasks

target = ''
%w[html pdf epub].each{|fmt|
  if targets.include? fmt
    target = ".#{fmt}_rst" 
  end
}

puts "target = #{target}"

contents = Dir.glob('*.erb').map{|f| f=~/(\w+)\.erb/ && $1}
contents.delete 'index'
puts "contents=#{contents.inspect}"

[:html, :qthelp, :epub, :pdf].each{|tgt|
  task tgt => contents.map{|c| "#{c}.#{tgt}_rst"} do |t|
    contents.each{|c|
      File.rename "#{c}.#{tgt}_rst", "#{c}.rst"
    }
    sh "make #{tgt}"
  end
}

directory 'images'

rule target => '.erb' do |t|
  File.open(t.name, 'w'){|f|
    erb = ERB.new(File.read(t.prerequisites.first))
    erb.result(binding).each_line{|l|
      if l =~ /http:\/\/alb\.anagix\.com:8180\/myGyazo\/data\/(.*.png)/
        image = $1
        Dir.chdir('images'){
          unless File.exist?(image)
            puts "wget #{l.chomp.strip}"
            system "wget #{l.chomp.strip}"
          end
        }
        f.puts "\n" + l.sub(/^/, '.. ')
        f.puts "\n.. image:: images/#{image}"
        f.puts '    :scale: 75%' # if target.include? 'html' 
#        f.puts '    :width: 3in' if target.include? 'pdf' 
        f.puts "    :target: #{l}"
      else
        f.puts l
      end
    }
  }
  puts "*** #{t.name} created"
end    
