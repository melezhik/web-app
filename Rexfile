use Rex::Misc::ShellBlock;

task "deploy", sub {
  shell_block <<'EOF';
    test -f ~/web-app/app.pid && kill `cat ~/web-app/app.pid`
    rm -rf ~/web-app
    git clone https://github.com/melezhik/web-app.git ~/web-app
    cd ~/web-app
    nohup plackup app.pl 1>nohup.log 2>&1 & echo -n $! > app.pid
EOF
};

