---
layout: post
title:04-25 In Class Notes [4/25/22]
---

# Week 4 Notes - Check in

**Remember:** always start with routes (user is taking an action, doing something that we don't want)
see what action was invoked and follow it thru, _use the server log_

**Partial Paths** (_ start with underscore)
<%= render @photo %> is basically doing <%= render @photo.to_partial_path %>
_in controller can only render main view template_
_in main view template can only render partials_

**Before Action(s)**
before changing classes in the controller look at before actions (before only exists in controllers)

_example_
```ruby
  def edit
    if @photo.owner != current_user
      redirect_back fallback_location: root_path, alert: "Nice try, suckah"
    end
  end
```
_redirect_back needs a fallback option in case the user just typed in the URL_
```ruby 
  before_action :ensure_owner_is_current_user, only: [:edit :update :destroy]

  def ensure_owner_is_current_user
    if @photo.owner != current_user
      redirect_back fallback_location: root_path, alert: "Nice try, suckah"
    end
```

_tip:_ for advanced associations -  has many through, whatever it is going through has to be defined above;
order of before actions matters

private keywords (convention) signals developers that these methods are only used in this class exclusively 
_ruby won't actually prevent them from calling these methods, but would give warning_
