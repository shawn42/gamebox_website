### Sound &amp; Music

SoundManager handles the autoloading of sounds from `data/sounds` and `data/music`. The stage has direct access via `sound_manager`. To allow an actor to emit sounds or music, give them the `audible` behavior.  See Reactions below for usage from actors.

{% highlight ruby %}
# music
sound_manager.play_music :overworld

# sounds
sound_manager.play_sound :death
{% endhighlight %}

Music will continue playing when scenes transition.  You could explicitly stop / start / change the music by calling `.stop_music :overworld`.  For example, let's say you wanted to have music in the main gameplay stage but then play pause menu music when the player presses ESC.

{% highlight ruby %}
define_stage :demo do
  curtain_up do
    sound_manager.play_music :game_music
    # ...
    # register key events or something that changes stages
  end
end

define_stage :pause_menu do
  curtain_up do
    sound_manager.stop_music :game_music
    sound_manager.play_music :pause_music
    # ...
  end
end
{% endhighlight %}

Sounds are placed in `data/sounds`.  Audio is handled by gosu and gosu supports ogg/wav/mp3 file formats as well as others.  Filenames are converted to symbols without the file extension.  For example:

{% highlight text %}
data/music/ambient.mp3
{% endhighlight %}

The file `ambient.mp3` would be played with `sound_manager.play_music :ambient`.  Files are accessed in alphabetical order.  If you have two files that have the same name, gamebox will use the first one.

{% highlight text %}
data/music/ambient.mp3
data/music/ambient.ogg
{% endhighlight %}

In this case with two files, `sound_manager.play_music :ambient` plays `ambient.mp3` only (because "m" in mp3 comes before "o" in ogg).  So name your files uniquely without relying on the file extension.  This is true of all gamebox assets.

Music files can only be played one at a time.  They won't mix.  If music is playing with the same name, playing it again won't restart it.  If you want to restart music, you can just stop/start it explicitly.
