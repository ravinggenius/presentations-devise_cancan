!SLIDE
.notes Initially all logic is placed in an `#initialize` method, however there is nothing stopping you from splitting permissions across many methods or even files
# Setup CanCan #

## Initialize permissions model ##
    @@@ bash
    $ rails generate cancan:ability

This creates a mostly empty model called `Ability`. Customize `initialize` to define permissions.


!SLIDE
.notes GOTCHA Projects with many controllers need to remember to secure all controllers
.notes Catch `CanCan::AccessDenied` to handle lack of permission
# Using CanCan #

## Helper methods for controllers and views ##
    @@@ ruby
    load_and_authorize_resource
    authorize_resource
    load_resource
    can?
    cannot?
    authorize!
    unauthorized!
    skip_load_and_authorize_resource
    skip_authorize_resource
    skip_load_resource

There are more. Check the documentation.


!SLIDE incremental
.notes `load_resource` (and `load_and_authorize_resource`) loads typical instance variables for each action
.notes The controller enforcest the permissions; `can?` only shows or hides appropriate view elements
# Using CanCan (continued) #

* Wrap links in the view with `if can? ...` checks.
* Setup a Role model and relate roles to users. `has_and_belongs_to_many` and `has_many :through` both come with caveats.


!SLIDE
.notes There are many options for customizing `load_resource` and friends (`:find_by`, `:class => false`, `class => 'MyUserClass'`, `:only`, `:except`, `:instance_name`)
# Advanced CanCan #

Customize finders when checking permissions or loading instance variables with `load_resource`. In your `Ability` class:
    @@@ ruby
    can :manage, Product, :discontinued => false
Then `:discontinued => false` will be used to scope any `Product` CanCan loads when checking *this* permission.
