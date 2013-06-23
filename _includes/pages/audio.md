### Sound &amp; Music

SoundManager handles the autoloading of sounds from `data/sounds` and `data/music`. The stage has direct access via `sound_manager`. To allow an actor to emit sounds or music, give them the `audible` behavior.  See Reactions below for usage from actors.

{% highlight ruby %}
# music
sound_manager.play_music :overworld

# sounds
sound_manager.play_sound :death
{% endhighlight %}
