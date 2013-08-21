### Purpose

Gamebox was designed to spring board game development. It allows the developer to define business rules about a game very quickly without having to worry about resource loading, sound/music management, creating windows, or messing with viewports. Gamebox allows you to define a game's business rules within minutes, using the metaphor of a 5th grade play.

[GRAPHIC: illustration of kids in costumes on a stage]

The driving idea behind Gamebox is to provide the ability to have as many of the basic common pieces of a 2D game at the developers disposal from the beginning.

{% highlight ruby %}

    # sample of defining the player's behaviors
    define_actor :player do
      has_behaviors do
        positioned
        audible
    
        grounded
        looker
    
        mover
        gibify
        slicer
        shooter recharge_time: 4_000, shot_power: 15, kickback: 1.4
        bomber kickback: 1.6
    
        die_by_sword
        die_by_bomb
        blasted_by_bomb
        disoriented_by_bombs
        die_by_bullet
        shielded
    
        pulled_by_black_hole
    
        jump max_power: 80, min_power: 20
      end
    end
{% endhighlight %}

### Games made with Gamebox
 * [Killbox](https://github.com/shawn42/killbox) - Local multiplayer gravity deathmatch.
  * [Lonely Shepherd](http://www.ludumdare.com/compo/ludum-dare-22/?action=preview&uid=571) - Ludum Dare 22 entry.
  * [Seed Life](http://www.ludumdare.com/compo/ludum-dare-26/?action=preview&uid=571) - Ludum Dare 26 entry
  * [OMG Aliens](https://github.com/shawn42/omg_aliens) - Space invaders clone.

### License

The MIT License (MIT)

Copyright &copy; 2013 Shawn Anderson

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
