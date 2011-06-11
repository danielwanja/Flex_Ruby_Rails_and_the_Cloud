!SLIDE commandline incremental
	$ heroku addons:add pusher:test
	Adding pusher:test to freezing-autumn-489... done, v7 (free)
	
* See http://pusher.com/docs/heroku
	
!SLIDE commandline smaller

# Add gem 'pusher' to your Gemfile
	$ bundle install

# Get your pusher api key
	
* Note: production is managed by heroku 
	
!SLIDE code smaller

# config/environments/development.rb
	
	@@@ruby
	require 'pusher'
	Pusher.app_id = 6182
	Pusher.key = 'a0b74a20a5d8df2db432'
	Pusher.secret = '057c1aac0e15defa3a55'
	
!SLIDE commandline incremental

	$ rails g controller Message hello	
	create  app/controllers/message_controller.rb
     route  get "message/hello"
    invoke  erb
    create    app/views/message
    create    app/views/message/hello.html.erb
    invoke  test_unit
    create    test/functional/message_controller_test.rb
    invoke  helper
    create    app/helpers/message_helper.rb
    invoke    test_unit
    create      test/unit/helpers/message_helper_test.rb

!SLIDE code smaller

	@@@ruby
	class MessageController < ApplicationController

	  def hello
	    Pusher['test_channel'].trigger('greet', {
	      :greeting => "Hello there!"
	    })    
	  end

	end
