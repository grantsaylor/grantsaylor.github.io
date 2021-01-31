---
layout: post
title:  "Magic Counter, an Android App"
date:   2021-01-31 12:21:00 -0800
categories: portfolio, android, kotlin
---

Magic Counter TCG is a native Android application written in Kotlin for Android version 8.0 and above. While searching for existing applications of this type, namely to count health in the popular card came, "Magic: The Gathering" I was dismayed to find many of them to be very simple and lacking the robust features that I myself wanted. After some tinkering I produced Magic Counter. 



<p style="float: left; font-size: 9pt; text-align: center; width: 30%; margin-right: 1%; margin-bottom: 0.5em;"><img src="/assets/magic_counter/magic_counter_main.jpg" style="width: 100%">The Main Screen of the App</p>
<p style="float: left; font-size: 9pt; text-align: center; width: 30%; margin-right: 1%; margin-bottom: 0.5em;"><img src="/assets/magic_counter/coinflipgif.gif" style="width: 100%">Flipping a Coin</p>
<p style="float: left; font-size: 9pt; text-align: center; width: 30%; margin-right: 7%; margin-bottom: 0.5em;"><img src="/assets/magic_counter/resetgame.gif" style="width: 100%">Resetting the Game Board</p>

In the three above screenshots you can see how the app-flow works. The user is presented with a board to toggle health, mana and induvidual mana colors. Health is given +1/-1 and +5/-5, incrementing and decrementing it accordingly. 

Similarly mana is given a +1/-1 but also +1/-1 to toggle each of the five elemental colors (blue, black, white, red and green.) Toggling any of those five colors will also trigger the main mana counter to increment or decrement. All of this is to allow the user a quick glance of their values. Oftentimes playing with many cards in the real world presents slowdown due to counting a large number of cards, Magic Counter eliminates this with easy to view content.

In the code snippet below you can see how I achieved the coin flip. I suppose it's quite simple in and of itself, but to give good user feedback I ensured that a Toast notification occured to signal that a coin flip occured. Because the coin flip is random, occasionally you will get multiple Heads/Tails in a row, visual feedback of a change in state was necessary.

{% highlight kotlin %}

//Set a click listener for the coinButton element.
coinButton.setOnClickListener {
            
            //The randomizer is between values 0 and 1.
            val randomizer = (0..1).random()
            
            //Toast when the button is clicked to signal a change.
            Toast.makeText(applicationContext, "Coin Flipped!", Toast.LENGTH_SHORT).show();
            
            //If the randomizer is equal to 1, it is a heads.
            if(randomizer == 1){
                coinFlip.text = heads
            }

            //If the randomizer is equal to 0, it is a tails.
            if(randomizer == 0){
                coinFlip.text = tails
            }

        }
{% endhighlight %}

Lastly the third screenshot shows the app resetting itself. It would be cumbersome to manually reset each toggle, so I included an option to simply tap a button and reset the entire game board to the default values.

While the app is simple overall, I wanted an application that made me feel I was in the world of Magic. To achieve this I searched high and low for the original type designer of the font "Goudy Medieval", [Dieter Steffmann][Steffmann], to ask permission to use his creation in my application, he graciously did. Please visit his website for a wealth of font knowledge. 


You can find the entire repository at [Magic Counter TCG][Magic Counter GitHub Repository] for more information.

---

Magic Counter (TCG) is unofficial Fan Content permitted under the Fan Content Policy. Not approved/endorsed by Wizards. Portions of the materials used are property of Wizards of the Coast. ©Wizards of the Coast LLC.

Wizards of the Coast Fan Content Policy: https://company.wizards.com/fancontentpolicy

Font "Goudy Medieval" used with express permission for commercial use by Dieter Steffman, creator of the font. (1/28/2021)


[Magic Counter GitHub Repository]: https://github.com/grantsaylor/Magic-Counter-TCG
[Steffmann]: http://www.steffmann.de/wordpress/
