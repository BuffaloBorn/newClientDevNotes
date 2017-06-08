# Notes
----
## Clients Gem Repo

| Name                        | Version | Comments                    |
|-----------------------------|---------|-----------------------------|
| Angular-rails               | 1.2.22  |                             |
| D3-rails                    | 3.3.9   |                             |
| twitter-bootstrap-rails     | 2.2.5   |                             |
| googlecharts                | 1.6.8   |                             |
| Swagger-ui-rails            | 0.1.3   |                             |
| bootstrap-growl-rails       |         |                             |
| ruby-growl.gem              | 4.0     |                             |
| jasmine                     | 2.0.2   |                             |
| jasmine-core                | 2.0.2   |                             |
| Jasmine-sprockets           | 0.3.2   |                             |
| jasmine fixtures            | 0.1.7   |                             |
| jasmine headless-webkit     | 0.8.4   |                             |
| jasmine jquery-rails        | 1.4.2   |                             |
| jasmine ajax                | 0.0.2   |                             |
| refinerycms-core            | 2.1     |                             |
| redis                       | 3.0.6   |                             |
| redis-store                 | 3.0.6   |                             |
| puma                        | 2.8.1   |                             |
| statistic2                  | 0.0.54  |                             |
| statsd-ruby                 | 1.2.1   |                             |
| Railes                      |         |                             |
| Jenkins war                 | 2.0.2   |                             |
| swagger-ui                  |         |                             |
| grape-swagger-rails         | 0.7.2   |                             |
| request-log-analyzer        |         |                             |
| state\_machine              | 1.2.0   |                             |
| state\_machine-audit\_trail | 0.1.3   |                             |
| devise                      | 3.5.6   |                             |
| echoe                       | 3.1.1   |                             |
| ember-rails                 | 0.15.0  |                             |
| faye                        | 0.8.9   |                             |
| faye-websocket              | 0.6.3   |                             |
| metric-fu                   | 4.11.4  |                             |
| fnoddmetric                 | 1.2.7   |                             |
| ruby-graphviz               | 1.2.2   |                             |
| workflow                    |         |                             |
| pry-debugger                | 0.2.3   |                             |
| ruby-debug-ide19            | 0.4.12  |                             |
| friendly\_id                | 5.0.4   |                             |
| dry-logic                   | ?       |                             |
| rbx-require-relative        | 0.05?   | Only works with ruby 1..8.7 |
| configatron                 | 2.9.1   |                             |
| configuration               | 1.3.4   |                             |
| ruport                      |         |                             |
| rubyzip                     |         |                             |
| Capybara-webkit             |         |                             |
| byebug                      |         |                             |
| figaro                      |         |                             |
| rawk\_log                   |         |                             |
| databaseclear               |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |
|                             |         |                             |

IDE and plugins

1.  Angular-eclipse-plugin -1.1.0

2.  AngularIDE – angular-ide-2012

3.  Aptana Studio 3 - &gt; 3.6.1

4.  Google.gdt.eclipse

5.  JSonEdit-repository – 0.9.7

6.  Edu.umd.cs.findbugs.plugin

AWS features

Cloudtail

Cloudtracker

CloudWatch – currently watching the video at client site and see how
they use

CI tools

Jenkins

GitHub

GitLabe

Environment setup

\# .bash\_profile

\# Get the aliases and functions

if \[ -f ~/.bashrc \]; then

. ~/.bashrc

fi

\# User specific environment and startup programs

PATH=$HOME/bin:$PATH

GEM\_HOME=$HOME/gems

GEM\_PATH=$HOME/gems

export LD\_LIBRARY\_PATH=$HOME/lib

export USERNAME BASH\_ENV PATH GEM\_HOME GEM\_PATH

wget http://www.sqlite.org/sqlite-autoconf-3070701.tar.gz

tar -zxvf sqlite-autoconf-3070701.tar.gz

cd sqlite-autoconf-3070701

./configure --prefix=$HOME

make && make install

cd $RAILS\_APP\_DIR

vi Gemfile

bundle config build.sqlite3 --with-sqlite3-include=$HOME/include
--with-sqlite3-lib=$HOME/lib --with-sqlite3-dir=$HOME/bin

bundle install --path vendor/bundle

Error installing sqlite3

yum install sqlite sqlite-devel

gem install sqlite3

Install a gem from a downloaded tar or zip

gem 'rails', :require =&gt; 'rails', :path =&gt; "/path\_to/rails"

**From: http://guides.rubygems.org/make-your-own-gem/\#introduction**

% tree

.

├── hola.gemspec

└── lib

└── hola.rb

% cat lib/hola.rb

class Hola

def self.hi

puts "Hello world!"

end

end

cat hola.gemspec

Gem::Specification.new do |s|

s.name = 'hola'

s.version = '0.0.0'

s.date = '2010-04-28'

s.summary = "Hola!"

s.description = "A simple hello world gem"

s.authors = \["Nick Quaranto"\]

s.email = 'nick@quaran.to'

s.files = \["lib/hola.rb"\]

\#or

\#s.files = \["lib/hola.rb", "lib/hola/translator.rb"\]

s.homepage =

'http://rubygems.org/gems/hola'

s.license = 'MIT'

end

gem build hola.gemspec

Successfully built RubyGem

Name: hola

Version: 0.0.0

File: hola-0.0.0.gem

% gem install ./hola-0.0.0.gem

Successfully installed hola-0.0.0

1 gem installed

% irb

&gt;&gt; require 'hola'

=&gt; true

&gt;&gt; Hola.hi

Hello world!

Useful GEM commands

| Command             | Short Describe                                       | Interesting options |
|---------------------|------------------------------------------------------|---------------------|
| gem environment     | Display information about the RubyGems environment   | --debug             |
| gem list            | Display local gems whose name matches REGEXP         | -all                |
| gem generate\_index | Generates the index files for a gem server directory |                     |
| gem help            | Provide help on the ‘gem’ command                    |                     |
| gem contents        | Display the contents of the installed gems           |                     |

Can't connect to local MySQL server through socket
'/var/run/mysqld/mysqld.sock'

If your file my.cnf (usually in the */etc/mysql/* folder) is correctly
configured with

socket=/var/lib/mysql/mysql.sock

you can check if mysql is running with the following command:

mysqladmin -u root -p status

try changing your permission to mysql folder. If you are working
locally, you can try:

sudo chmod -R 755 /var/lib/mysql/

that solved it for me

are you sure you installed mysql as well as mysql server..

-   For example to install mySql server I'll use yum or apt to install
    both mysql command line tool and the server:

yum -y install mysql mysql-server (or apt-get install mysql
mysql-server)

Enable the MySQL service:

/sbin/chkconfig mysqld on

Start the MySQL server:

/sbin/service mysqld start

afterwards set the MySQL root password:

mysqladmin -u root password 'new-password' (with the quotes)

I hope it helps.

-   **Re: Can't connect to local MySQL server through socket
    '/var/run/mysqld/mysqld.sock' (2) \[SOLVED\]**

1.  /etc/init.d/mysql stop.

2.  mysqld\_safe --skip-grant-tables &

3.  mysql -u root.

4.  use mysql;

5.  update user set password=PASSWORD("NEW-ROOT-PASSWORD") where
    User='root';

6.  flush privileges;

7.  quit.

Integration Research

Checkout how apache layout and hooks into rails

Remove Linux folder: rm -rf mydir

Rename: mv /home/user/oldname /home/user/newname (maybe \[-T\])

Figure out what .rz stands for

The .rz extension files are compressed with the inflate algorithm. The
Marshal version number comes from ruby’s Marshal::MAJOR\_VERSION and
Marshal::MINOR\_VERSION constants. It is used to ensure compatibility.

For gem generate\_index --directory /path/to/repo, expose /path/to/repo
via your HTTP server configuration (not /path/to/repo/gems).

When done, it will generate a set of files like this:

gems/\*.gem \# .gem files you want to

\# index

specs.&lt;version&gt;.gz \# specs index

latest\_specs.&lt;version&gt;.gz \# latest specs index

prerelease\_specs.&lt;version&gt;.gz \# prerelease specs index

quick/Marshal.&lt;version&gt;/&lt;gemname&gt;.gemspec.rz \# Marshal
quick index file

Current project GEM list (GEMFILE entries)

| Name                  | Version | Comments |
|-----------------------|---------|----------|
| Ws-auth               |         |          |
| Activerecord          |         |          |
| Coffee-script         |         |          |
| Rails                 |         |          |
| Mysql2                |         |          |
| Sass-rails            |         |          |
| Uglifer               |         |          |
| Coffee-rails          |         |          |
| Jquery                |         |          |
| Turbrolinks           |         |          |
| Jbuilder              |         |          |
| Sdoc                  |         |          |
| To\_xls               |         |          |
| Sal-audit             |         |          |
| Bcrypt                |         |          |
| Unicorn               |         |          |
| Capistrano-rails      |         |          |
| Byebug                |         |          |
| Web-console -&gt; 3.0 |         |          |
| Spring                |         |          |
| request-log-analyzer  |         |          |

JavaScript Frameworks

| Name                         | Version | Comments |
|------------------------------|---------|----------|
| Angular-ui-ng-grid           |         |          |
| Bootstrap-3.0.2              |         |          |
| DataTables-1.10.4            |         |          |
| DataTables-bootstrap         |         |          |
| Jqplot                       |         |          |
| Jquery-1.10.2                |         |          |
| Jquery-easyui 1.4            |         |          |
| Jquery-ui 1.10.3             |         |          |
| Jquery-ui 1.10.4             |         |          |
| Jquery-ui multiselect-widget |         |          |
| Themes                       |         |          |
| Yui                          |         |          |
| Parley-js-master             |         |          |

Installing rails and supporting tools

-   bundle –v

-   gem install rails --no-ri –no-rdoc

-   which bundle

-   rbenv rehash

-   rails –v

-   mysql –version

-   which mysql

-   install mysql

-   mysql –u root

-   mysqladmin –u root password

-   gem install mysql2

-   rails new simple\_cms –d mysql

-   rails server

-   stop server (control z)

-   rails g controller demo index

Rails 5 gems that caused issue in deploy

| Name              | Available Version | Needed Version | Comments |
|-------------------|-------------------|----------------|----------|
| In nio4r          | 1.0.1             | ~&gt; 1.2      |          |
| websocket-driver  | 0.3.0             | ~&gt; 0.6.1    |          |
| rails-dom-testing | 1.0.7             | ~&gt; 2.0      |          |
| rack              | 1.6.4             | ~&gt;2.0       |          |
| arel              | 6.0.3             | ~&gt; 7.0      |          |

Provide Configuartion options nokogiri\_1.6.7.2

1.  yum gcc ruby\_devel zlib-devel mysqldevel

2.  3.  4.  Sudo yum install –y rubygem-nokogiri

Yum command is responding with the following

Another app is currently holding the yum.lock

Run the following commands:

-   ps aux | grep yum

-   kill \[pid\]

-   cd /var/run/

-   rm –f yum.pid

-   yum update

Serving Multiple Rails Apps under One Virtual Host with Phusion
Passenger

Two Rails apps, both of which needed to be hosted under a single domain
- one served from root, and the other from a directory. Here was an
ideal setup:

-   app1 deployed to /apps/app1/current at mydomain.com

-   app2 deployed to /apps/app2/current at mydomain.com/app2

This is easily accomplished with Passenger, but took some tinkering to
figure out. Here’s how two ended up with:

&lt;VirtualHost \*:80&gt;

ServerName mydomain.com

DocumentRoot "/apps/app1/current/public"

RailsEnv production

&lt;Directory "/apps/app1/current/public"&gt;

Options Indexes FollowSymLinks -MultiViews

AllowOverride All

Order allow,deny

Allow from all

&lt;/Directory&gt;

&lt;Directory /apps/app1/current/public/app2&gt;

Options Indexes FollowSymLinks -MultiViews

AllowOverride All

Order allow,deny

Allow from all

&lt;/Directory&gt;

RackBaseURI /app2

&lt;/VirtualHost&gt;

Apache is now properly configured. All that remains is a little setup in
the apps themselves. Since the Apache config expects a Rack/Rails app at
/apps/app1/current/public/app2, you just need to create a symlink in
/apps/app1/current/public to app2:

ln -s /apps/app2/current/public app2

Depending upon your deployment strategy, you may need to create the
symlink each time you deploy. I setup a symlink as part of the
capistrano deploy and everything just worked™.

**Bonus**: If you use a common datastore and session\_store key within
your Rails applications, you can share authentication between the two
apps to create a cohesive “logged-in” interface.

Deploy an app to a sub-URI or subdirectory

You can also deploy an app to a sub-URI instead of the root URI. For
example, suppose that you already have a virtual host for the
application /websites/phusion:

&lt;VirtualHost \*:80&gt;

ServerName www.phusion.nl

DocumentRoot /websites/phusion/public

&lt;Directory /websites/phusion&gt;

Allow from all

Options -MultiViews

\# Uncomment this if you're on Apache &gt;= 2.4:

\#Require all granted

&lt;/Directory&gt;

&lt;/VirtualHost&gt;

And you want your application, located in /websites/secondapp, to be
accessible from the URL http://www.phusion.nl/subpath. To do this, you
need to perform the following:

-   Set Alias {SUBURI} {PATH TO YOUR APPLICATION'S PUBLIC DIRECTORY}.

-   Create a &lt;Location /{SUBURI}&gt; block.

-   Inside the Location block, set PassengerBaseURI /{SUBURI}.

-   Inside the Location block, set PassengerAppRoot {PATH TO YOUR
    APPLICATION ROOT}.

-   Create a &lt;Directory {PATH TO YOUR APPLICATION PUBLIC
    SUBDIRECTORY}&gt; block.

-   Inside the Directory block, set Allow from all, and (if you’re on
    Apache &gt;= 2.4) Require all granted.

-   Inside the Directory block, disable MultiViews.

Here is an example:

&lt;VirtualHost \*:80&gt;

ServerName www.phusion.nl

DocumentRoot /websites/phusion/public

&lt;Directory /websites/phusion&gt;

Allow from all

Options -MultiViews

\# Uncomment this if you're on Apache &gt;= 2.4:

\#Require all granted

&lt;/Directory&gt;

\# These have been added:

Alias /subapp /websites/secondapp/public

&lt;Location /subapp&gt;

PassengerBaseURI /subapp

PassengerAppRoot /websites/secondapp

&lt;/Location&gt;

&lt;Directory /websites/secondapp/public&gt;

Allow from all

Options -MultiViews

\# Uncomment this if you're on Apache &gt;= 2.4:

\#Require all granted

&lt;/Directory&gt;

&lt;/VirtualHost&gt;

When you are done, restart Apache:

sudo apachectl restart

(Depending on your operating system, the right command may be apache2ctl
instead of apachectl.)

You are now done. If you run into any problems, please refer to the
[troubleshooting
guide](https://www.phusionpassenger.com/library/admin/apache/troubleshooting/).

[Configure in Apache two Ruby on Rails apps in the same Server with same IP](https://serverfault.com/questions/370594/configure-in-apache-two-ruby-on-rails-apps-in-the-same-server-with-same-ip)
=================================================================================================================================================================================================

&lt;VirtualHost \*:80&gt;

\#ServerAdmin @dummy-host.example.com

DocumentRoot /webserver/myapp/public

ServerName myapp-Development

&lt;Directory /webserver/myapp/public&gt;

AllowOverride all

Options -MultiViews

&lt;/Directory&gt;

ErrorLog logs/k2-error\_log

CustomLog logs/k2-access\_log common

&lt;/VirtualHost&gt;

&lt;VirtualHost \*:3000&gt;

\#ServerAdmin @dummy-host.example.com

DocumentRoot /webserver/myapp2-admin/public

ServerName myapp2-admin

&lt;Directory /webserver/myapp2-admin/public&gt;

AllowOverride all

Options -MultiViews

&lt;/Directory&gt;

\#ErrorLog logs/k2-error\_log

\#CustomLog logs/k2-access\_log common

&lt;/VirtualHost&gt;

| check my answer [here](https://serverfault.com/a/410351) to a similar question about serving multiple rails applications from sub-url's.  
                                                                                                                                            
 If you want to server your two rails apps from two different ports, apart from the virtual host, you have to also add to your apache conf  
                                                                                                                                            
 Listen 80                                                                                                                                  
                                                                                                                                            
 Listen 3000                                                                                                                                
                                                                                                                                            
 NameVirtualHost \*:80                                                                                                                      
                                                                                                                                            
 NameVirtualHost \*:3000                                                                                                                    |
|-------------------------------------------------------------------------------------------------------------------------------------------|

**Dealing with Included configuration files within the httpd.conf file**

Make sure to review all the files that can be included within the
following directory conf.d, conf.modules.d or any other configuration
folder that is instructed by using the IncludeOptional directive. Using
mod\_ssl in SSL.conf

**Tunneling to remote server resource and allowing local IDEs like MySQL
Workbench to connect remotely**

Create a batch file and place the following putty command and augments
inside:

../putty –L \[localPort\]:\[remoteservername\]:\[remotePort\] unser

[How to have multiple versions of Ruby AND Rails, and their combinations on Windows?](http://stackoverflow.com/questions/3648744/how-to-have-multiple-versions-of-ruby-and-rails-and-their-combinations-on-windo)
=================================================================================================================================================================================================================

Refer to this page:
<http://stackoverflow.com/questions/3648744/how-to-have-multiple-versions-of-ruby-and-rails-and-their-combinations-on-windo>

Make that this create and used:

echo 3 - Ruby 2.0.0 (64 bit)

choice /C 123 /M "Which Ruby? "

if errorlevel 255 goto confused

if errorlevel 3 goto 3

if errorlevel 2 goto 2

if errorlevel 1 goto 1

if errorlevel 0 goto 0

goto confused

:1

if exist c:\\ruby rmdir c:\\ruby

if exist c:\\devkit rmdir c:\\devkit

mklink /j c:\\ruby c:\\ruby193

mklink /j c:\\devkit c:\\devkit-4.5.2

goto end

:2

if exist c:\\ruby rmdir c:\\ruby

if exist c:\\devkit rmdir c:\\devkit

mklink /j c:\\ruby c:\\ruby2-x86

mklink /j c:\\devkit c:\\devkit-x64

goto end

:3

if exist c:\\ruby rmdir c:\\ruby

if exist c:\\devkit rmdir c:\\devkit

mklink /j c:\\ruby c:\\ruby2-x64

mklink /j c:\\devkit c:\\devkit-x64

goto end

:confused

echo I'm confused ...

:end

ruby -v

**Updating ruby gems with internet access in window but organization has
an internal gem repository **

Remember to check the current set gem source with the version of ruby
that is being used. For example run the following command:

$ gem sources

Next, remove all the default sources and replace with the known
organization repository with the following commands:

$ gem source -r https://rubygems.org/

$ gem source -u

$ gem source –a https://\[ organization url\]

$ gem source -u

**Rails environment configuration management**

Received code that used the following syntax:

Config::CONFIG\[‘target\_os’\]

And it was not execute as expected in rails 4.2.4. After some web
searching, I discovered that I need to reference rbconfig library as the
following

require ‘rbconfig’

Config :: CONFIG\[‘some\_rails\_env\_propetry’\]

and located the following gems that may provide the same functionality
but different syntax:

-   Configatron

-   Configutation

[Inline-CSS-Extractor](https://github.com/peterlazzarino/Inline-CSS-Extractor) 
===============================================================================

<img src="./media/image1.png" width="624" height="287" />
=========================================================

<img src="./media/image2.png" width="624" height="245" />
=========================================================

<img src="./media/image3.png" width="624" height="259" />
=========================================================


