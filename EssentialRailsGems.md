## Essential Rails Gems

Ruby on Rails is a great framework for quickly and easily building applications for the web. It's a framework designed with developer productivity and happiness in mind. However, there are lots of commonly required features that Rails doesn't support out of the box. You can always roll your own solutions, but the best case is to use a community-created gem.

In this course, Tuts+ instructor José Mota will show you how to use some of the most commonly needed gems for Rails apps. You'll learn about gems that improve the debugging experience, that help with user authorization and authentication, that run tasks, perform search, protect data and more! You'll also learn about some really crucial testing gems along the way.

#### 1.1 Introduction

Welcome to Essential Rails Gems! In this lesson I’ll explain the idea behind this course and talk a little about the projects that we will explore while learning about some key gems for development with Ruby on Rails.

###### Related Links
* [Get Started With Ruby on Rails: Source Code](http://github.com/tutsplus/get-started-with-ruby-on-rails)


#### 2.1 Better Errors

In this lesson you’ll learn about the better_errors gem, which enhances the error page in Rails. Whenever an unexpected exception shows up, it’s displayed in the browser. With better_errors, the experience is much improved with a better user interface and extra information such as local variable state.

###### Related links
* [Better Errors on GitHub](https://github.com/charliesome/better_errors)

#### 2.2 Bullet

The problem with N+1 queries is that they slow your application significantly. Removing these performance bottlenecks allows your apps to be more sustainable in the long run. Bullet allows you to identify and correct these inefficient queries.

###### Related links
* [Bullet on GitHub](https://github.com/flyerhzm/bullet)

#### 2.3 Letter Opener

Testing outgoing email is usually a chore. Using letter_opener will make outgoing email easier to test and will prove to be a invaluable asset to your development.

###### Related links
* [Letter Opener on GitHub](https://github.com/ryanb/letter_opener)

#### 2.4 Devise

A user model is almost always necessary for any serious application. Devise takes on the responsibility of creating that user model. In this lesson, you’ll learn how to set up a user model and how to address the common use cases of logging in and signing up.

###### Related links
* [Devise on GitHub](http://github.com/plataformatec/devise)

#### 2.5 Pundit

Along with user authentication, authorization is another feature that you’ll need in order to determine who can or cannot perform specific actions in your app. Pundit tackles this challenge in a rather interesting way.

###### Related links
* [Pundit on GitHub](https://github.com/elabs/pundit/)

#### 2.6 Carrierwave

File uploading is a common task for web applications. Doing so in Ruby might not be so easy—unless you’re doing it right, that is, with Carrierwave!

###### Related links
* [Carrierwave on GitHub](http://github.com/carrierwaveuploader/carrierwave)
* [Install ImageMagick With Homebrew on Mac OS X](http://brewformulas.org/Imagemagick)
* [Install ImageMagick in Ubuntu](https://help.ubuntu.com/community/ImageMagick)

#### 2.7 Kaminari

For large applications with lots of data, pagination is a necessity. Kaminari comes to the rescue in a really comfortable, meaningful fashion. In this lesson, I’ll show you how to integrate Kaminari in your Rails app.

###### Related links
* [Kaminari on GitHub](https://github.com/amatsuda/kaminari)
* [Bootstrap Theme for Kaminari on GitHub](https://github.com/matenia/bootstrap-kaminari-views)

#### 2.8 Sunspot

When your site or app has a large volume of data, search functionality can help make up for the difficulty of finding content scattered around your app. In this lesson, I’ll show you how to use Sunspot for search with drop-in capabilities for your Active Record models.

###### Related links
* [Sunspot Homepage](http://sunspot.github.io/)
* [Install Java](https://java.com/en/download/)
* [Searchable Methods in Sunspot](https://github.com/sunspot/sunspot#setting-up-objects)

#### 2.9 Paranoia

When you need something to prevent your data from being destroyed, Paranoia might be a justified response. In this lesson, I’ll show you how to use Paranoia to protect your application data from being deleted from your database. Active Record will be modified so that destroying a record causes it to be "soft deleted”—a special deleted_at field will be set, and the record will be hidden from the rest of your app.

###### Related links
* [Paranoia on GitHub](https://github.com/radar/paranoia)

#### 2.10 ActiveAdmin

Managing data in your application is an important task. One way to access and manage your Rails app data is through ActiveAdmin, a Rails engine that runs separately from the core of your app to give you full control over your data.

###### Related links
* [ActiveAdmin on GitHub](http://github.com/activeadmin/activeadmin)
* [On Using ActiveAdmin and Sunspot Together](http://mrdanadams.com/2012/beware-using-active_admin-and-sunspot-rails-gems-together)

#### 2.11 Sidekiq

Running tasks in background processes is something that not everyone thinks about at the beginning of developing an application, but the need for a separate process to handle heavy lifting might come up later. In this lesson, I’ll show you how Sidekiq can be used as a task runner.

###### Related links

* [Sidekiq on GitHub](http://github.com/mperham/sidekiq)
* [Install Redis on Mac OS X](https://medium.com/@petehouston/install-and-config-redis-on-mac-os-x-via-homebrew-eb8df9a4f298)
* [Install Redis on Ubuntu](http://linuxg.net/how-to-install-redis-server-3-0-0-on-ubuntu-14-10-ubuntu-14-04-ubuntu-12-04-and-derivative-systems/)
* [Install Redis on Windows](https://github.com/ServiceStack/redis-windows#readme)

#### 3.1 Hirb

Testing and debugging often involves reading information in the console. Hirb is a small but special utility that enhances your console sessions. In this lesson, I’ll show you how Hirb can help display ActiveRecord objects and all sorts of lists in a more readable fashion.

###### Related links

  * [Hirb on GitHub](https://github.com/cldwalker/hirb#readme)

#### 3.2 DatabaseCleaner

Part of a good test suite is the ability to isolate test runs. DatabaseCleaner ensures that the database remains clean after each run, as I’ll show you in this lesson.

###### Related Links

  * [DatabaseCleaner on GitHub](https://github.com/DatabaseCleaner/database_cleaner)

#### 3.3 FactoryGirl

When it comes to spawning objects for testing, using a factory is a whole lot easier than just manually creating objects. In this lesson, you’ll learn how to set up FactoryGirl in order to build and persist objects in your test suite.

###### Related Links

  * [FactoryGirl on GitHub](http://github.com/thoughtbot/factory_girl)

#### 3.4 Timecop

Ever wanted to test a particular feature that depends on some time having elapsed? Timecop lets you manipulate time itself! Learn how to use this library in order to test time-sensitive code.

###### Related Links

  * [Timecop on GitHub](https://github.com/travisjeffery/timecop)

#### 3.5 Pry

A Ruby console is usually run within an IRB session. Pry is a drop-in replacement for IRB with extra features baked in, such as tab completion, debugging and code navigation capabilities. In this lesson, you’ll learn how you can use Pry to enhance your interactive console experience. I’ll also show you how Pry integrates with Rails and with byebug, a Ruby debugger.

###### Related links

  * [Pry on GitHub](https://github.com/pry/pry)
  * [Pry-rails on GitHub](https://github.com/rweng/pry-rails)
  * [Pry-byebug on GitHub](https://github.com/deivid-rodriguez/pry-byebug)

#### 3.6 Minitest and RSpec for Rails

In this lesson you'll learn about how to integrate the two most widely used testing frameworks for Ruby: MiniTest and RSpec. MiniTest is easy to integrate with a new Rails app. As for RSpec, the procedure is slightly more difficult, but still quite manageable. In this lesson I'll show you how to either RSpec or MiniTest with a Rails app.


#### 4.1 Conclusion

Thanks for watching to the end of this course on essential Rails gems. If you have any questions or feedback, visit our community forum or send us a tweet. See you soon!
