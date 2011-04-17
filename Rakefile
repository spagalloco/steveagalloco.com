require 'rubygems'
require 'yaml'

desc 'Upload the site'
task :deploy do
  require 'net/scp'
  config = YAML.load_file('site.yml')
  REMOTE_DIR = config['remote_path']

  Net::SCP.start(config['hostname'], config['username'], :password => config['password']) do |scp|
    scp.upload! 'index.html',     REMOTE_DIR
    # scp.upload! 'assets',         REMOTE_DIR, :recursive => true
    scp.upload! 'images',         REMOTE_DIR, :recursive => true
    scp.upload! 'src',            REMOTE_DIR, :recursive => true
    scp.upload! 'stylesheets',    REMOTE_DIR, :recursive => true
  end
end
