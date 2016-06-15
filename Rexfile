use Rex::Misc::ShellBlock;
use Rex::CMDB;

set cmdb => { type => 'YAML', path => 'cmdb' };
require Rex::Misc::Sparrow;

task "deploy", sub {
  shell_block <<'EOF';
    test -f ~/web-app/app.pid && kill `cat ~/web-app/app.pid`
    rm -rf ~/web-app
    git clone https://github.com/melezhik/web-app.git ~/web-app
    PATH=/home/melezhik/perl5/bin:$PATH
    cd ~/web-app
    nohup plackup app.pl 1>nohup.log 2>&1 & echo -n $! > app.pid 
EOF
};


task set_spl => sub {
  file "~/sparrow.list",
    content => template(
      'files/sparrow.list', 
      list => { 'web-app-check' => 'https://github.com/melezhik/web-app-check.git' } 
    );
};

