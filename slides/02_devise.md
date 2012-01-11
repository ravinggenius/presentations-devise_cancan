!SLIDE
.notes Devise will create the model and inject some default configuration. Some options require fields in the database. Inspect the model and associated migration before blindly running `$ rake db:migrate`
# Setup Devise #

## Initialize and create or modify a model
    @@@ bash
    $ rails generate devise:install
    $ rails generate devise user

Name your model whatever you please. It will be created if it is not found.

## Files to notice
    @@@
    app/models/user.rb
    config/initializers/devise.rb
    db/migrate/n{16}_devise_create_users.rb


!SLIDE
.notes Helper methods are based on the name of the model(s) you are using with Devise
# Using Devise #

## Helper methods for controllers and views
    @@@ ruby
    before_filter :authenticate_user!
    current_user
    user_signed_in?
    user_session

## ... and tests
    @@@ ruby
    sign_in
    sign_out


!SLIDE incremental
# Advanced Devise #

* Subclass `Devise::SessionsController` to override default behavior
* Customize views by running `$ rails generate devise:views`
