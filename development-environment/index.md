---
layout: default
title: MTD Front-End Docs / Development Environment
---

# Development Environment Setup

## For Windows Machines

### 1. Download and Install Ruby 2.0

* Download and install - [http://rubyinstaller.org/downloads/](http://rubyinstaller.org/downloads/)

During the install process, be sure to check "Add Ruby executables to your PATH"

### 2. Download and Install Ruby 2.0 Development Kit under "Other Useful Downloads"

* Download and install - [http://rubyinstaller.org/downloads/](http://rubyinstaller.org/downloads/) 
* Unzip the file
* At command prompt, cd into the directory where you unzipped the files
* Type "ruby dk.rb init"
* Type "ruby dk.rb install"

### 3. Download and Install RubyGems

* Download and install - [http://rubygems.org/pages/download](http://rubygems.org/pages/download)
* Grab the zip and unzip the file
* Open command prompt, go to the directory where extracted rubygems is and run "ruby setup.rb".

### 4. Download and Install Git 

* Download and install - [https://git-scm.com/download/win](https://git-scm.com/download/win)
* During install select to "Use Git Bash only"

### 5. Install Bundler gem

* If you haven't cloned the repo yet, see the [Repository section](/repository) first
* Change directories to the mtd-shared-checkout folder
* Type "gem install bundler"

### 6. Install gem dependencies

* Change directories to mtd-shared-checkout
* Type "bundle install"

### 7. Run the web app

* Type "thin -R config.ru start"
* View app at "http://localhost:4567/troybilt" 