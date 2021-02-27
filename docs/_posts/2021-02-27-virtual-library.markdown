---
layout: post
title:  "Virtual Library, An Easy to Use Android Application"
date:   2021-02-27 11:47:00 -0800
categories: portfolio, android, kotlin
---

Virtual Library is an application written in Kotlin for Android devices such as phone or tablet. The goal of the project is to create a software overlay for existing "Little Free Libraries" in your neighborhood, giving you access to a circulation system akin to what you would see at your county library. 

Working as a the project lead, myself and my three teammates set out to create an app that would transform an already popular system into something that simpler and easier to use.

In this post I'll be talking about components that I personally worked on.

<p style="float: left; font-size: 9pt; text-align: center; width: 30%; margin-right: 1%; margin-bottom: 0.5em;"><img src="/assets/virtual_library/vlTitleScreen.gif" style="width: 100%">The Main Screen of the App</p>
<p style="float: left; font-size: 9pt; text-align: center; width: 30%; margin-right: 1%; margin-bottom: 0.5em;"><img src="/assets/virtual_library/vlMapScreen.gif" style="width: 100%">The Map Scren</p>
<p style="float: left; font-size: 9pt; text-align: center; width: 30%; margin-right: 7%; margin-bottom: 0.5em;"><img src="/assets/virtual_library/vlCheckoutScreen.gif" style="width: 100%">The Checkout Screen</p>
<p style="float: left; font-size: 9pt; text-align: center; width: 30%; margin-right: 7%; margin-bottom: 0.5em;"><img src="/assets/virtual_library/vlUserScreen.gif" style="width: 100%">The User Screen</p>

In the four above screenshots above you can see the various components of the application, the main, map, checkout and user screens. Each one presents the user with vital information.

On the main screen the user is presented with a scrolling carousel of books that have been recently added to a library, this will change periodically. There are options to view libraries in your area, search for books (in your locale), view your profile and delete/or sign out of the app. 

Moving to the map screen you are presented with the ability to add a library to the map, view a library, toggle favorite locations, etc. This screen utilizes the Google Maps API and Firebase database to complete its tasks. This is useful to finding out what is near you. When tapping on a library you are presented with that location's circulation of books.

I wanted this app to feel like you were in an old library, we opted for a distinct visual flair that would keep you immersed in the world of Virtual Library, for that reason you can see our checkout screen is lush with detail, such as the baroque frame surrounding the camera viewfinder. 
This viewfinder is used to scan ISBN numbers to checkin/out a book/add a book to your personal collection/or add a book to your library. It is context sensitive. This will speak with the OpenLibrary API and Firebase database to complete the transcation. 

Utilizing the Firebase database the app is able to display user-specific information on your profile, such as favorites and personal collection. This is great way to see what other users are interested in!
Technologies on the user screen include event handlers and asynchronous database use. 

In the code snippet below I will display how map regenration occurs. After the Google Maps API service is up and running, the event handler sets up the marker parameters by pulling all the present libaries from the database, inserting them into an array. After this occurs the regeneration method takes that information to display the same content for every user.
{% highlight kotlin %}

//Set a click listener for the coinButton element.
private fun regenerateMarkers(){
        for(element in markerArray){
            val regenLatLng = LatLng(element.elementAt(0), element.elementAt(1))
            //Place the marker
            mapGeneration.addMarker(
                    //Set params for when you tap the marker
                    MarkerOptions()
                            .position(regenLatLng)
                            .title(name)
                            .snippet(libararyContent)
                            .icon(BitmapDescriptorFactory.fromResource(R.mipmap.ic_user_location))
            )
        }
    }
{% endhighlight %}


This is an app built from the ground up for a service that did not exist in the way we wanted it to and I believe we have accomplished our goals of making a world-rich app for free libraries in your neighborhood.
