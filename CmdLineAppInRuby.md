## Command Line Applications In Ruby

Welcome to the “Command-Line Apps with Ruby” course! This course will get you up and running on how to build fantastic applications for the command line, using the Ruby language.

In this course, we’ll cover two awesome frameworks: Thor and GLI. They are similar in context but serve different crowds and purposes. You’ll learn the differences between the two and when to use each one.

#### 1.1 Introduction

In this lesson you’ll be given the agenda and installation notes to get your prepared to take the course.

#### 1.2 Command line Features

Before we delve in too deep, it’s important that you grasp the most basic aspects of command-line applications, they have key aspects that make their development and use so unique.

In this lesson we’ll take a look at some examples of scripts and applications so you can see how they work so you can build an application of your own.

#### 2.1 Hello World with Thor

The first framework that we’ll cover is Thor. It is a framework that builds command-line applications with ease. It is used by many other applications, one of them being Ruby on Rails.

In this lesson, we’ll dip our feet in the water by building a rather simple Hello World example.

#### 2.2 Thor Options and Arguments

Now that you know how to bootstrap an app with Thor, we’ll introduce more complexity in this lesson by passing in options and arguments to our application. You’ll learn how Thor parses the information you type in the prompt and transforms it into the various elements that belong to the app.

#### 2.3 Thor Subcommands

When you strive to build a more complex application, you might consider grouping certain features of your application into some sort of scope.

In this lesson we’ll pick up on where we left in the previous lesson and implement subcommands in our Thor app. They are just as any other command, except they live in a named scope.

#### 3.1 Introduction to GLI

This lesson begins a new chapter and it introduces a new tool: GLI. It was developed with the purpose of creating a standard in Ruby CLI application development. It introduces a big set of conventions and it strives to accomplish a perfect workflow with low boilerplate.

In this lesson we’ll explore a newly generated GLI app and we’ll build a Hello World command.


#### 3.3 GLI Subcommands

GLI’s nature is to be the ultimate application framework. To achieve this status, it considers the possibility to group similar features into contexts.

In this lesson you’ll learn how to understand and implement subcommands in a GLI app.

#### 4.1 Interactivity with Highline

This chapter covers some libraries that orthogonally extend your command line applications, meaning they will work regardless of using either Thor, GLI or nothing at all.

This lesson will introduce Highline, a gem that allows you to request information from the keyboard. You’ll learn the different methods available to gather and process information from the standard input.

#### 4.2 Testing with Aruba

Aruba is a Cucumber extension that allows you to write acceptance tests against your command-line application. With this tool you will be to assert on files and directories being created, check if a certain output is printed to the screen and many more features.

#### 4.3 Coloring with Rainbow

Have you ever noticed how hard it is to color something in a bash script? Well you don’t need to worry about that with Ruby because Rainbow makes it dead easy and cool to print colored output into your screen.

In this lesson we’ll learn how to use Rainbow to print formatted output.

#### 4.4 Formatted Tables with Terminal-Table

I recall one gem that empowers the `rails console` utility and allows it to print tabular information on ActiveRecord data.

This lesson will introduce you to Terminal-Table, a gem that builds tables to be printed to the screen.

#### 5.1 Build a CLI App

This is the moment of truth. We’ll be building an application from scratch using most of the material we’ve learned in this course, writing tests first and printing colored tables. Are you ready?

#### 5.2 Final Tips

I hope you have enjoyed the contents of this course. If you have faced any problems or got stuck somewhere trying to replicate the exercises in the videos, please give us a shout at the forums, we’ll be very glad to help you.

See you soon, it’s been great to have you!
