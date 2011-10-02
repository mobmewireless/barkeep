require "rake/testtask"
require "resque/tasks"

$LOAD_PATH.push("./") unless $LOAD_PATH.include?("./")

task :test => ["test:units", "test:integrations"]

namespace :test do
  Rake::TestTask.new(:units) do |task|
    task.libs << "test"
    task.test_files = FileList["test/unit/*"]
  end

  Rake::TestTask.new(:integrations) do |task|
    task.libs << "test"
    task.test_files = FileList["test/integration/*"]
  end
end

namespace :resque do
  desc "Start running all resque workers."
  task :start do
    puts `script/resque_workers.rb start`
  end

  desc "Stop running all resque workers."
  task :stop do
    puts `script/resque_workers.rb stop`
  end
end

namespace :clockwork do
  desc "Start running periodic jobs."
  task :start do
    puts `script/clockwork_jobs.rb start`
  end

  desc "Stop running periodic jobs."
  task :stop do
    puts `script/clockwork_jobs.rb stop`
  end
end