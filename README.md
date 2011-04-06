About : 
=========
WhaTV is a simple information diffusion system, aimed to be used either in web
browsers or embedded in entreprise diffusion systems.


Install :
=========
To simply try WhaTV, clone it and activate submodules :
$ git clone git://github.com/WaterCooled/WhaTV
$ cd WhaTV
$ git submodule init
$ git submodule update

You then need a simple webserver (apache, ngninx, lighttpd...) to run it.

If you want to modify it, fork it with github or another git utility.

You can also view it online from a (slow) webserver : 
http://whatv.watercooled.org

Changelog :
=========

0.0.1 (2010-09-11)
----------------
Initial release.
[Cedric de Saint Martin]

0.0.2 (2010-09-11)
----------------
Iframe and video full support with proper css.
[Cedric de Saint Martin]

0.0.3 (2010-09-11)
----------------
Adding Flash support.
[Cedric de Saint Martin]

0.0.4 (2010-10-18)
----------------
Adding modular Ambimage support.
[Cedric de Saint Martin]

0.0.5 (2010-10-19)
----------------
Get rid of majority of jquery calls,
Ambilight support,
Adding an options system to specify image and video options (not fully implemented)
[Cedric de Saint Martin]

0.0.6 (2010-10-23)
----------------
Option system with (fullscreen, ambimage/ambilight, crop) options, every size calculated relatively for images and video,
Everything is vertically centered.

0.0.7 (2010-10-25)
----------------
Introducing a footer with a clock and a Quick Messages system.
[Cedric de Saint Martin]

0.1.0 (2010-10-25)
----------------
First stable release with proper "finished loading" event firing, no timeout for videos
[Cedric de Saint Martin]

0.2.0 (2010-10-27)
---------------
Adding a new, more robust system for managing slides, each slide is 
monitored, if something goes wrong, we can know it instantaneously.
Adding a new container system : each slide has its own container div (was:
two global div, alterning)
[Cedric de Saint Martin]

0.2.1 (2011-01-05)
---------------
Fixing video bugs, cleaning code, works with Firefox
[Cedric de Saint Martin]

0.2.2 (2011-01-17)
---------------
Adding fullscreen support
[Cedric de Saint Martin]

0.2.3 (2011-01-17)
---------------
Better handling of bad video slide
[Cedric de Saint Martin]

0.2.4 (2011-01-17)
---------------
Adding Youtube videos Support
[Cedric de Saint Martin]

0.2.5 (2011-01-19)
---------------
Adding public methods to our object, allowing to go to next slide,
pause a video, and adding a callback which will be called to send
information about each slide.
[Cedric de Saint Martin]

0.5.0 (2011-01-19)
---------------
Major refactoring, separating 'core' code to 'modules' and utilities.
Adding a simple API to add and customize 'modules' (fullscreen, ambilight, etc)
Adding reference implementations of base modules, and examples of modules
[Cedric de Saint Martin]

0.5.1 (2011-03-31)
----------------
Add correct implementation of WhaTV.core.pause() and WhaTV.core.resume()
Fix bug where messages and date were disappearing when showing Flash slide
Solved several bugs on various platforms
[Cedric de Saint Martin]


Roadmap :
=========
0.5.x : Widgets support
0.5.x : Proof of concept : meteo widget
0.5.x : First implementation of transitions
0.6.0 : Modular transition system with some examples
0.7.0 : Powerpoint support
0.9.9 : documentation, API and examples
1.0.x : Posting server, dynamic fetching of resources from server, maybe use of http://www.w3.org/TR/FileAPI/
1.1.x : Optional authentication system
2.0.x : Video overlay

Ideas :
separate css from logic in QuickMessages
Header + animated header
Photo album module
CSS3 image animation support (examples : http://developer.apple.com/safaridemos/showcase/transitions/) 
Module system, where we specify urls of extensions files + http://requirejs.org/
quick message system : titles
flv videos
Fetch from time to time the new list of slides to show
http://net.tutsplus.com/tutorials/tools-and-tips/learn-how-to-develop-for-the-iphone/

Known Bugs : 
 - Youtube plugin does not work (due to Flash security restrictions) unless server is at localhost
 - Quick Messages animations are uglily slow when showing resource-intensive video
 - Date CSS is ugly and vary from browsers
 - Chrome : timeout is not respected in videos
 - Someone reported that loop is stopped somewhere (before video?) (J�r�my)
 - Under webkit : videos cause HUGE leaks
 - Broken div are not garbage collected.



Public API Documentation
===============
WhaTV provides an interface to interact with slides. Here is the documentation of the methods contained in this interface.

 - WhaTV.core.version() : returns the current version of the WhaTV system.
 - WhaTV.core.next() : skip the currently shown slide, and shows the next one.
 - WhaTV.core.pause() : Pause the current slide, preventing the system from going to the next slide. Also pauses the playing video, if any.
 - WhaTV.core.resume() : Either resume a paused video or go to the next slide if pause() was previously called.
 - WhaTV.core.registerInformationsListener(f) : Adds the function "f" to a list of listeners. Each time the system goes to the next slide, it calls each function in the list with an object as parameter describing the new slide (type, location, length, description, etc) (TODO : describe this object).