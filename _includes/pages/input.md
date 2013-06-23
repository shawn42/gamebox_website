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
