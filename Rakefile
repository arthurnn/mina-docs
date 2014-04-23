# Okay!
#
# rake deploy version=0.1.1

ENV['github'] ||= 'mina-deploy/mina'
# ENV['analytics_id'] ||= 'UA-32476157-1'

task :build do
  cmd = "bundle exec middleman build --debug"
  cmd = "analytics_id=#{ENV['analytics_id'].inspect} #{cmd}" if ENV['analytics_id']
  system cmd
  raise "Failed" unless $?.to_i == 0
end

desc "Updates online documentation"
task :deploy => :build do
  cmd = "git update-ghpages #{ENV['github']} -i build"
  cmd << " -p #{ENV['version']}" if ENV['version']
  system cmd
end
