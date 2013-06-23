### Actor Views

- rendering overview
- layers &amp; parallax
- defining actor views
- setting view on an actor (non magic name)
- custom renderer (here, stages, or advanced)

Actor views are the mechanism for drawing an actor in Gamebox. When an actor is created, Gamebox will see if there is a matching actor view by name. It will register the view to be drawn by the renderer. The draw callback is called with the rendering target, the x and y offsets based on the viewport, and the z layer to be used for drawing this actor (see the section on parallax layers for more on z layers).

{% highlight ruby %}
define_actor_view :label_view do
  draw do |target, x_off, y_off, z|
    target.print actor.text, actor.x, actor.y, z, actor.font_style
  end
end
{% endhighlight %}
