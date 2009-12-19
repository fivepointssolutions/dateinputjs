desc 'Launch the testing server on port 4000'
task :server do
  cd 'test' do
    `serve` # Requires http://github.com/jlong/serve
  end
end

desc 'Remove the dist directory'
task :clean do
  rm_r 'dist'
end

desc 'Assemble files for distribution'
task :package => [:clean] do
  mkpath 'dist'
  readme = IO.read('README')
  readme = "/*\n" + readme.split("\n").map { |line| " * #{line}" }.join("\n") + "\n *\n */\n\n"
  statusjs = IO.read('src/javascripts/dateinput.js')
  open('dist/dateinput.js', 'w') do |f|
    f.write(readme + statusjs)
  end
  cp_r 'src/images', 'dist'
  cp 'src/stylesheets/dateinput.css', 'dist'
end