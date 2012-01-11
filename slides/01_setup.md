!SLIDE
# Devise and CanCan #

authentication and authorization


!SLIDE incremental
# Devise #

* robust and easy to configure authentication framework
* works out of the box with Rails (almost)
* supports third party authentication OAuth2 via Omniauth
* full I18n support and more


!SLIDE incremental
.notes CanCan allows you define authorization however you like
# CanCan #

* authorization based on roles, groups etc
* more setup then Devise, but still easy
* single location for editing permissions


!SLIDE
.notes Stick this in your `Gemfile`
# Installation #

    @@@ ruby
    gem 'cancan'
    gem 'devise'
