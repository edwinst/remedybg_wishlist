# Intro

This is my wishlist for features in George Menhorn's new great, little "remedybg" debugger
(see [remedybg on itch.io](https://remedybg.itch.io/remedybg) and [remedybg on the handmade network](https://remedybg.handmade.network/)).
You should definitely check it out if you're a programmer working on x64-Windows!

All these wishes are just that: wishes and at most suggestions. I understand
that feature creep needs to be guarded against. I have therefore tried to suggest features that
make it easier to "outsource" more fancy stuff to external applications (e.g. by having good access to
clipboard functions in all views) and to suggest simpler alternatives for some more complex wishes.

[remedybg issue tracker on github](https://github.com/x13pixels/remedybg-issues/issues)

## About myself

Unsurprisingly, I'm a programmer myself and you can see me using remedybg and
writing "handmade" C++ code on [twitch](https://www.twitch.tv/edwinst) and
[YouTube](https://www.youtube.com/channel/UC2FDMyhLAoQM2HR8zY4m7hw).

## The list

I assigned the following subjective priorities:

*   **(1)**   important
*   **(nth)** "nice to have"
*   **(use)** usability & enjoyment maximization (ALSO IMPORTANT :-)
*   **(eye)** cosmetics, eye candy

**Note:** Strong emphasis **like this** in the following is only meant to help the reader with orientation and is not to be read as **SHOUTING**! ;-)

# All debug views (e.g. Modules, Threads, Call Stack, Memory, Disassembly):

*   **(1)** As a minimum of interactivity, **all text in the tables in these views should be exportable (copy-able) to the clipboard**.

    Maybe copy the whole text with one click/context menu option/hotkey as a
    tab-separated/comma-separated text table and optionally also copy a single
    table cell.  (Partial selection & copy is nice but lower priority.)

    **Note:** This allows the user to use searching features, analysis features in other applications quickly as long
    as they are not provided by remedybg itself. Single-cell copy will be very useful with calculators like [speedcrunch](https://speedcrunch.org/).

    **Example:** The Modules view is almost unusable without such features, I'm afraid. The Memory view would gain a lot of possibilities.

    **Idea:** As an advanced version of this feature, auto-copy of a single selected cell to the clipboard after
    each step could be very useful.

    **Idea:** Long-term, I could imagine remedybg to expose some low-level native API to a hot-loaded DLL into which
    the user can put ad-hoc code that does interesting analysis on view contents / debug data after stepping, etc..

*   **(use) For table cells which are only shown partially, show the full cell contents if possible on mouse-over** in
    the status line or *in a separate full-width line at the bottom of the window*, a line which can maybe be disabled for people
    who want to optimize vertical screen space.

    **Note:** I think I'd like this better than showing text in pop-ups / "tooltips" as is done now for the EFLAGS register.
    A dedicated line for such mouse-over text would minimize distraction of the user, text running off-screen, etc..
    Also, importantly: Such a separate mouse-over-line could work nicely while stepping if one leaves the mouse
    hovering over the same spot. *Motto: Left hand/keyboard for stepping, right hand/mouse for inspection, similar to how it
    is done in games.* (*Apropos:* How about some stepping short-cuts on the left side of the keyboard, under the relaxed
    left hand position? Like W/S for step over/into and E/D for the instruction versions?)

# All tabbed views

*   **(use)** I always find that having **the closing "X" on every tab causes usability issues**. When one flicks quickly
    through the tabs it is too easy to close one accidentally, which is annoying. I'd prefer having a "Close"
    option on a right-click context menu on the tab. (It is also Huffman coding: closing is much rarer than switching tabs, isn't it?)

*   **(use)** Keyboard navigation is generally very good already but it is not as easily discoverable as it could be.
    One idea: To the right of the tab headers there is often unused space.--If this space is wide enough, display a string there
    (in a low contrast gray) saying "Switch with Alt", for example. I don't know if one could do something similar for Ctrl-Tab,
    though the latter one is a more standard shortcut for doing that kind of thing, so it is not so important.

*   **(use)** It is a bit surprising that after keyboard navigation through the tabs with Alt, a tab can only be
    confirmed and opened by pressing Space, not with Enter. Maybe allow Enter, too?

# All menus

*   **(eye)** for the selected menu option, the contrast is very bad for the hotkey text to the right of the option.
    Would be nice to make it white on light blue or so.

*   **(use)** The tolerance for moving the mouse pointer to the right and down into a submenu without the submenu disappearing
    is there but it is relatively tight. Especially with neighboring entries like Window > Style and Window > Save layout,
    I'd enjoy a slightly more tolerant reaction to the pointer movements.

# Session menu

*   **(use, nth) tab completion for filenames** in target, directory, and argument boxes

*   **(use) Maybe display the list of recent sessions closer to the "Recent" menu option (and the user's pointer)**

    **Note:** The (very nice) direct entry of the executable path, etc., has the one disadvantage that the menu becomes quite wide.
    This makes for an awkwardly long mouse movement from "Recent" to the actual list. For very wide menus it might be better to
    open the submenu below and only slightly to the right (to expose enough of the menu text) of the pointer instead of to the very right of the whole menu.

# Process control, image and symbol loading

*   **(use) Display an error message if the loaded image has been linked incrementally** and therefore will not work in remedybg (do not fail silently).

    **Note:** Currently I have some images which remedybg loads without complaining but then breakpoints and stepping
    will silently not work. This can be quite confusing.

*   **(use) When the process exits, there should be a notice in the status bar** (best: green for exit status 0, red for != 0).

    **Note:** Currently it can be confusing for the user if the process exits and the "Output" tab is not visible.
    Also, remedybg is so blazingly fast that sometimes one does not even notice that it has already reacted to F5
    and executed the whole process to completion :-).

# Source view

*   **(use)** Go-to-line (Ctrl-G) works fine but is not discoverable via the "Source File" menu. Adding it there would help new users. _Fixed in 0.3.0.6_

*   **(use)** Run-to-cursor and Set-next-statement should maybe be discoverable
    via the "Control" menu. Do you think the menus would get too long this way?
    I'm not sure. As a user, I think I'm also fine with learning that in this
    application, I also should use the context menu for shortcut discovery,
    though.

# Watching variables and expressions

*   **(1) A faster way to add watched expressions that occur in the source.**

    **Ideas:** single-word expressions could be added by double-clicking.
    Text selection and right-click>(context option) or a hotkey would work even for more complicated expressions.

*   **(1) Quick search feature (breadth-first) in the watch expressions tree / forest.**

    **Note:** As a vim-mer, I'd love incremental search started by pressing
    '/'. Windows-y Ctrl-F would be fine and less surprising, though.
    Maybe the most difficult part of this feature is how to gracefully
    handle descending into collapsed structs during incremental search. For a
    first version, non-incremental would already be great. (Maybe with incremental first result display in the "mouse-over-line"?)

    **Note:** A depth-first search starting at the selected node could also be useful but I'd guess breadth-first
    is the more usually needed case.

*   **(1) Array inspection within structs and in "\_\_locals".** A quick way to inspect arrays hanging off pointers in structs and from local variables would be great.

    **Ideas:** Have a "+" button next to each pointer which turns the watch item into "...,2", "...,3", "...,4", etc. with 1,2,3 clicks.
    This way one could easily inspect the first few elements. For a larger number of elements one can do "Add Watch", then add the comma and
    and number. Maybe "Add watch" could automatically open the new watch item in edit mode with the cursor at the end?

    ALTERNATIVE to "Add watch": With the 3rd click, the "+" button could turn into an entry field for the number of array elements. This
    would solve the problem of how to reduce the number of items, too.

    For decreasing the number, one could have a '-' button or edit mode for nested items (a bigger, more complicated and controversial topic, I guess)
    or a context menu option.

    **Note:** Mid-term, a dedicated "Array inspection" view could be useful for large arrays in order to display arrays in matrix style similar to Memory,
    but typed and interpreted. This would not replace the quick inspection mentioned above, though.

*   **(use)** Make it more obvious that one can add new items by clicking below the last watch item.
    (Use all space below the last item as a mouse "area of attack" for this and put text or button there to tip the user off.)

*   **(use)** Allow expanding/collapsing of watched structs e.g. by double-click on the name to increase the area of attack for collapsing/expanding.

     **Note:** For the root items, this currently collides with the edit-on-double-click. Maybe it would be fine
    to toggle expansion along with the editing? After all, what I want to edit, I usually also want to see, right?
    A click on the collapse button could then re-collapse and also quit the
    editing, which seems useful. Would need to be tried to see if is a good
    idea, I guess.

*   **(nth)** "__autos" struct which works similar to Visual Studio "Autos"
    watch window (shows variables used around the current source line and
    return values of recently returned functions).

    **Note:** The __autos features can be rather nice but if it introduces a lot of complexity, I'd be fine without it.
    Adding a very quick way to add watches (like double-click or right-click>(context option) on the name in the source) would go
    a long way to making __autos not needed. Return values could be displayed with less effort, maybe.

# Memory view

*   **(1)** The possibility to **keep multiple (or at least 2) memory views open at different addresses** would be great.

# Disassembly view

*   **(1) This view desperately needs navigation. Minimum: go to address/symbol.**

*   **(eye) -> (use)** Use (maybe only slightly) different colors for address, machine code bytes, disassembly, respectively.

    **Note:** This becomes a usability feature in cases where the machine code bytes "bleed" into the disassembly column.

# Register view

*   **(use) Color changed register values** after stepping.

*   **(use)** Offer "add to watch" context menu option to make it more obvious that that is (already) possible.

*   **(use)** On mouse-over on a register, show multiple interpretations of the register bits in the mouse-over-text-line discussed above,
    e.g. split off lower 32/16 bits, show decimal signed and unsigned interpretations (maybe ASCII character for lowest 8 bits or even 8 ASCII characters for a 64-bit registers?).

