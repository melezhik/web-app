use Rex::Misc::ShellBlock;

task "deploy", sub {
  shell_block <<'EOF';
    test -f ~/web-app/app.pid && kill `cat ~/web-app/app.pid`
    rm -rf ~/web-app
    git clone https://github.com/melezhik/web-app.git
    cd web-app
    nohup plackup & echo -n $! > app.pid
EOF
};

