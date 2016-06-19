Caltrain.info
=============

A quick experiment in displaying [Caltrain's schedule](http://www.caltrain.com/schedules/weekdaytimetable.html) using 24 hour time.

Every time I look at the schedule I have to do,

*    find the "Schedules" menu in its 11px font on the busy main page
*    mouse over and select "Weekday" or "Weekend"
*    scroll around the giant schedule
*    constantly re-orient because the confusing and ambiguous AM/PM system doesn't provide fast clues as to which part of the schedule you're looking at

None of these is a serious UX flaw but in combination and multiplied by having to go through it every. single. time. got old.

"But you could use bookmarks, browser completion, and remember that AM/PM is distinguished by bold and italic on the page!"

Sure, or we could just have a single page that doesn't need any of that: [Caltrain.info](http://www.caltrain.info)

*    **24 hour clock**
*    home page is the weekday schedule
*    big, prominent link to weekend
*    removed UI clutter
*    (links back to caltrain.com work)

## Approach

I didn't want to start messing around with the HTML manually so I used jQuery to adjust the DOM from a single place in the code. This way when the schedule is updated it'll be much easier to apply these changes to it.

The schedule uses multiple `td:nth-child` to turn columns italic or bold for AM and PM. When the schedule rolls over from 11PM to 12AM, however, it has to "fix" them and does that, frustratingly, using `span`s (instead of say, `class="pm"` or setting the style on the `td` directly...), so I couldn't figure how to easily use the computed style while resetting it cleanly.

Caveat: I'm not a regular JavaScript programmer so school me ;-)

Alternatives: Caltrain, to their credit, has a developer page with a [GTFS](https://en.wikipedia.org/wiki/General_Transit_Feed_Specification) feed: [Caltrain GTFS](http://www.caltrain.com/developer.html). Presumably the plethora of iOS and Android apps use this. For a lot more than these 3-4 hours you could build your own schedule page I guess! Ironically the feed is in 24 hour time ;-)





