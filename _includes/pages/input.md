### Input &amp; Updates

- input manager
- director for updates

Input comes from the InputManager. The stage has direct access via the `input_manager` method. Behaviors can request that they get the `input_manager` via `requires :input_manager`. The preferred way of getting input to your actors is via the actor's `input` method. It returns an InputMapper that can be built with a hash of events. Behaviors then subscribe for those events from the actor's input, or ask for it during updates.

{% highlight ruby %}
actor.input.map_input '+space' => :shoot,
                      '+w' => :jump,
                      '+a' => :walk_left
                      '+s' => :duck
                      '+d' => :walk_right

actor.input.when :shoot do
  # shoot code
end

# or
if actor.input.walk_left?
  # walk left
end
{% endhighlight %}

The stage has access to the InputManager via the input_manager object that is in scope.  For example, if we explicitly wanted to make the ESC key fire the pause menu stage, we could do this:

{% highlight ruby %}
define_stage :flying do

  curtain_up do
    # ...
    input_manager.reg :down, K_ESCAPE do
      fire :change_stage, :pause_menu
      # be sure to explicitly list your stages in config/environment.rb
      # so gamebox knows what :pause_menu is
    end
    # ...
  end
end
{% endhighlight %}

The listing of key input constants is in `gamebox/lib/gamebox/constants.rb` but here are a few to give you an idea:

{% highlight text %}
K_RETURN  K_A  K_B  K_C  K_ESCAPE  K_SPACE  K_RSHIFT  K_LSHIFT
{% endhighlight %}

In order to use these shorthand K_ constants, `require 'gamebox/constants'` in `config/environment.rb`.
