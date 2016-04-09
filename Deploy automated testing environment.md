# Deploy automated testing environment

## 1. Install Ruby

Execute command `ruby -v` in terminal to check Ruby version. If it does not work or the version is less than 1.9.3, you should install Ruby manually.

### Ubuntu Linux / OS X / ...

1. Install system dependence

  - Ubuntu Linux 
    1. required to install `libssl-dev`, `libreadline-dev` and `libffi-dev`.
    ```bash
    $ sudo apt-get install libssl-dev libreadline-dev libffi-dev
    ```

    2. clone rbenv and its plugins to `~/.rbenv`
    ```bash
    $ # copy all following content to terminal
    git clone git://github.com/sstephenson/rbenv.git ~/.rbenv
    git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
    git clone git://github.com/jamis/rbenv-gemset.git  ~/.rbenv/plugins/rbenv-gemset
    git clone git://github.com/sstephenson/rbenv-gem-rehash.git ~/.rbenv/plugins/rbenv-gem-rehash
    git clone https://github.com/rkh/rbenv-update.git ~/.rbenv/plugins/rbenv-update
    ```

    3. add content to `~/.bashrc` (zsh: `~/.zshrc`)
    ```bash
    # ruby
    export PATH="$HOME/.rbenv/bin:$PATH"
    eval "$(rbenv init -)"
    ```

  - OS X
  *(you should be a user with root, e.g. 1⃣sudo passwd root 2⃣the passwd of current user 3⃣your new root passwd)*
    1. required to install [Xcode](http://developer.apple.com/xcode/) and [Homebrew](http://brew.sh/).

    2. install by Homebrew
    ```bash
    $ brew install readline rbenv ruby-build rbenv-gemset rbenv-gem-rehash
    ```

    3. add content to `~/.bash_profile` (zsh: `~/.zshrc`)
    ```bash
    # ruby
    export RBENV_ROOT=/usr/local/var/rbenv
    if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
    ```

2.  Install Ruby by [rbenv](https://github.com/sstephenson/rbenv)

    ```bash
    # open a new terminal
    
    # list all available versions
    $ rbenv install --list
    
    # install specified version
    $ rbenv install 2.1.6
    
    # config Ruby version
    $ rbenv global 2.1.6
    ```

### Windows

1. Install Ruby

    - [RubyInstaller](http://rubyinstaller.org/downloads/)

    - [chocolatey](https://chocolatey.org/packages/ruby)

        ```bash
        # administrative PowerShell
        C:\> choco install ruby
        ```

2. [Install Development Kit](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit#installation-instructions)

## 2. Update [RubyGems](https://rubygems.org/)
```bash
$ # copy all following content to terminal
gem sources --remove https://rubygems.org/
gem sources --add https://ruby.taobao.org/
gem update --system
gem rdoc --all --overwrite
gem update
gem install bundler
```

## 3. [Bundle](http://bundler.io/) install
```bash
# Change directory to this project in terminal

# check comments and install dependence of some specified gems
$ cat Gemfile

# install all required gems
$ bundle install
```
