# Ferdinando Santacroce's blog
This is my personal blog, available at [jesuswasrasta.com](https://jesuswasrasta.com).  

# Credits
[Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/)

# Handy references
Minimal Mistakes Theme
* [Minimal Mistake template - Quick Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/)
* [When you have some doubts on formatting or so](https://mmistakes.github.io/minimal-mistakes/year-archive/)

I use the [Remote theme method](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remote-theme-method).  
To update the theme, see [upgrading guide](https://mmistakes.github.io/minimal-mistakes/docs/upgrading/#remote-theme).  

Jekyll
* [Jekyll Docs](https://jekyllrb.com/docs/home/)  
* [Using Jekyll as a static site generator with GitHub Pages](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/)

Markdown
* [Kramdown Syntax](https://github.com/Stamplay/docs/wiki/Kramdown-Syntax)


# Tips, FAQs and WTFAQs
Here a collection of tips, FAQs and things I discovered while setting up this blog.

## Jekill
[Jekyll](https://jekyllrb.com) website has a very well-done docs section; I followed this guide, [Jekyll on Windows](https://jekyllrb.com/docs/windows/).  
I went for [Installation via Bash on Windows 10](https://jekyllrb.com/docs/installation/windows/#installation-via-bash-on-windows-10).  

### Running the blog locally
Prerequisites: a valid installation of Jekyll.  
1. Navigate to your blog folder  
2. Run `bundle exec jekyll serve`; it will run your blog at [localhost:4000](http://localhost:4000)

Using `bundle exec jekyll serve --incremental` will reload your `_config.yml` when it changes.  

### Problem: bundle install fails because of nokogiri
Installation done with `bundle install` encountered a problem with `nokogiri`:  
~~~
$ bundle install
...[omissis]...
Fetching nokogiri 1.8.2
Installing nokogiri 1.8.2 with native extensions
Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

current directory:
/mnt/c/D/Source/Github/jesuswasrasta/jesuswasrasta.github.io/vendor/bundle/gems/nokogiri-1.8.2/ext/nokogiri
/usr/bin/ruby2.3 -r ./siteconf20180501-67-1svnupg.rb extconf.rb
checking if the C compiler accepts ... yes
Building nokogiri using packaged libraries.
Using mini_portile version 2.3.0
checking for gzdopen() in -lz... no
zlib is missing; necessary for building libxml2
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.

Provided configuration options:
        --with-opt-dir
        --without-opt-dir
        --with-opt-include
        --without-opt-include=${opt-dir}/include
        --with-opt-lib
        --without-opt-lib=${opt-dir}/lib
        --with-make-prog
        --without-make-prog
        --srcdir=.
        --curdir
        --ruby=/usr/bin/$(RUBY_BASE_NAME)2.3
        --help
        --clean
        --use-system-libraries
        --enable-static
        --disable-static
        --with-zlib-dir
        --without-zlib-dir
        --with-zlib-include
        --without-zlib-include=${zlib-dir}/include
        --with-zlib-lib
        --without-zlib-lib=${zlib-dir}/lib
        --enable-cross-build
        --disable-cross-build

To see why this extension failed to compile, please check the mkmf.log which can be found here:

/mnt/c/D/Source/Github/jesuswasrasta/jesuswasrasta.github.io/vendor/bundle/extensions/x86_64-linux/2.3.0/nokogiri-1.8.2/mkmf.log

extconf failed, exit code 1

Gem files will remain installed in
/mnt/c/D/Source/Github/jesuswasrasta/jesuswasrasta.github.io/vendor/bundle/gems/nokogiri-1.8.2 for inspection.
Results logged to
/mnt/c/D/Source/Github/jesuswasrasta/jesuswasrasta.github.io/vendor/bundle/extensions/x86_64-linux/2.3.0/nokogiri-1.8.2/gem_make.out

An error occurred while installing nokogiri (1.8.2), and Bundler cannot continue.
Make sure that `gem install nokogiri -v '1.8.2'` succeeds before bundling.

In Gemfile:
  github-pages was resolved to 183, which depends on
    jekyll-mentions was resolved to 1.3.0, which depends on
      html-pipeline was resolved to 2.7.2, which depends on
        nokogiri
~~~
{: .language-shell}

#### Solution: install these dependencies
I solved installing these packages:  
`sudo apt-get install gcc ruby-dev libxslt-dev libxml2-dev zlib1g-dev`  
After this, command `bundle install` ends successfully.  

### Problem: rake not installed
Rake is _make for Ruby_: [Rake](https://github.com/ruby/rake).  
It deals with `Rakefile` files; Jekyll uses it to assemble all the _sources_ and make the actual website.  

#### Solution: install it
Install it with `sudo apt install rake`.  
Then install the Ruby gem `sudo gem install rake`

### Problem: Jekyll serve fails
Jekyll can serve your website locally, to let you develop and test the results.  
You can start up a local webserver running the command `jekyll s` inside the folder of your repositry: 
~~~
~/jesuswasrasta.github.io$ jekyll s
~~~

In my PC, this raised this error:  
~~~
~/jesuswasrasta.github.io$ jekyll s
/var/lib/gems/2.3.0/gems/bundler-1.16.1/lib/bundler/runtime.rb:313:in `check_for_activated_spec!': You have already activated public_suffix 3.0.2, but your Gemfile requires public_suffix 2.0.5. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
        from /var/lib/gems/2.3.0/gems/bundler-1.16.1/lib/bundler/runtime.rb:31:in `block in setup'
        from /usr/lib/ruby/2.3.0/forwardable.rb:202:in `each'
        from /usr/lib/ruby/2.3.0/forwardable.rb:202:in `each'
        from /var/lib/gems/2.3.0/gems/bundler-1.16.1/lib/bundler/runtime.rb:26:in `map'
        from /var/lib/gems/2.3.0/gems/bundler-1.16.1/lib/bundler/runtime.rb:26:in `setup'
        from /var/lib/gems/2.3.0/gems/bundler-1.16.1/lib/bundler.rb:107:in `setup'
        from /var/lib/gems/2.3.0/gems/jekyll-3.8.0/lib/jekyll/plugin_manager.rb:50:in `require_from_bundler'
        from /var/lib/gems/2.3.0/gems/jekyll-3.8.0/exe/jekyll:11:in `<top (required)>'
        from /usr/local/bin/jekyll:22:in `load'
        from /usr/local/bin/jekyll:22:in `<main>'
~~~

