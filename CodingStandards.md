# Code layers and unit testing #
Snap's code is very roughly divided into three layers:
  * The front end, which is the GUI part
  * The middle end, which ties the GUI and back end together
  * The back end, which does all the real work

The front end cannot be unit tested in a reasonable way, so we don't bother. Instead, what we do is make the front end as trivial as possible; the middle end tells the GUI what to do, and relays commands from the GUI to the back end. This is much easier to test than putting all GUI-related stuff in the front end.

Note that the distinction between "middle end" and "back end" is very blurry, and is largely just a convention for emphasizing the decoupling of display logic from the front end. By contrast, the distinction between the front end and the other layers should be very clear.

All code in both the middle end and the back end needs to be covered by unit tests. We try to code each unit test before actually writing the code to be tested (i.e., test-driven development). Reading the existing tests should give you an idea of how it's done; also try googling for test-driven development, or read books such as Test-Driven Development by Example, by Kent Beck, or Test-Driven Development: A Practical Guide.

Note that neither the middle end nor the back end should ever need to `import wx` or use any wxPython classes. All that stuff goes in the front end.


# Comments #
Not many should be necessary. Most of the code's real documentation is in the form of choosing good variable/method names, good function interfaces, and unit tests. We think that these make for much better documentation than comments ever could, and the best part is, they'll never go out of date.

However, algorithms, as opposed to code itself, may need to be documented. (As a hypothetical example, if you don't know how quicksort works, you may have trouble figuring out how it works from the code alone, no matter how well-written it is.) These should probably be documented here on the wiki if it isn't a well-known algorithm.


# Other #
  * Use `from __future__ import division` in all non-trivial modules, even if no division currently takes place in that module.
  * Always use new-style classes.
  * Use spaces, not tabs.
  * Constants are `LIKE_THIS`.
  * Class names are `LikeThis`.
  * Function/method names are `likeThis`, except in classes derived from wxPython classes, where they are `LikeThis` for consistency. For names that are `likeThis`, try to make the first word a verb.