# Intro

This is my wishlist for features in George Menhorn's new great, little remedybg debugger
(see [remedybg on itch.io](https://remedybg.itch.io/remedybg) and [remedybg on the handmade network](https://remedybg.handmade.network/)).
You should definitely check it out if you're a programmer working on x64-Windows!

All these wishes are just that: wishes and at most suggestions. I understand
that feature creep needs to be guarded against. I have therefore tried to suggest features that
make it easier to "outsource" more fancy stuff to external applications (e.g. by having good access to
clipboard functions in all views) and to suggest simpler alternatives for some more complex wishes.

## About myself

I'm a programmer myself and you can see me using remedybg and writing "handmade" C++ code on [twitch](https://www.twitch.tv/edwinst) and [YouTube](https://www.youtube.com/channel/UC2FDMyhLAoQM2HR8zY4m7hw).

## The list

I assigned the following subjective priorities:

*   **(0)**   showstopper *[none hit so far, phew :-)]*
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

    **Example:** The Modules view is almost unusable without such features, I'm afraid.

    **Idea:** Long-term, I could imagine remedybg to expose some low-level native API to a hot-loaded DLL into which
    the user can put ad-hoc code that does interesting analysis on view contents after stepping, etc..

*   **(use) For table cells which are only shown partially, show the full cell contents if possible on mouse over** in
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
    option on a right-click context menu on the tab. (It is also Huffman coding: closing is much rarer than switching tabs.)

# All menus

*   **(eye)** for the selected menu option, the contrast is very bad for the hotkey text to the right of the option.
    Would be nice to make it white on light blue or so.

# Session menu

*   **(use, nth) tab completion for filenames** in target, directory, and argument boxes

# Process control, image and symbol loading

*   **(use) Give error message if the loaded image has been linked incrementally** and therefore will not work in remedybg (do not fail silently).

    **Note:** Currently I have some images which remedybg loads without complaining but then breakpoints and stepping
    will silently not work. This can be quite confusing.

*   **(use) When the process exits, there should be a notice in the status bar** (best: green for exit status 0, red for != 0).

    **Note:** Currently it can be confusing for the user if the process exits and the "Output" tab is not visible.
    Also, remedybg is so blazingly fast that sometimes one does not even notice that it has already reacted to F5
    and executed the whole process to completion :-).

# Watching variables and expressions

*   **(1) A faster way to add watched expressions that occur in the source.**

    **Ideas:** single-word expressions could be added by double-clicking.
    Text selection and right-click>(context option) or a hotkey would work even for more complicated expressions.

*   **(1) Quick search feature (breadth-first) in the watch expressions tree.**

    **Note:** As a vim-mer, I'd love incremental search started by pressing
    '/'. Windows-y Ctrl-F would be fine and less surprising, though.
    Maybe the most difficult part of this feature is how to gracefully
    handle descending into collapsed structs during incremental search. For a
    first version, non-incremental would already be great.

    **Note:** A depth-first search starting at the selected node could also be useful but I'd guess breadth-first
    is the more usually needed case.

*   **(1) Array inspection within structs and in "\_\_locals".**

    **XXX** note to myself: describe this feature!

*   **(use)** Make it more obvious that one can add new items by clicking below the last watch item.
    (Use all space below the last item as a mouse "area of attack" for this.)

*   **(use)** Allow expanding/collapsing of watched structs e.g. by double-click to increase the area of attack for collapsing/expanding.

     **Note:** For the root item, this currently collides with the edit-on-double-click. Maybe it would be fine
    to toggle expansion along with the editing? After all, what I want to edit, I usually also want to see, right?
    A click on the collapse item could then re-collapse and also quit the editing, which seems useful.

*   **(nth)** "__autos" struct which works similar to Visual Studio "Autos" watch window (shows variables used around the current source line and return values of recently returned functions).

    **Note:** The __autos features can be rather nice but if it introduces a lot of complexity, I'd be fine without it.
    Adding a very quick way to add watches (like double-click or right-click>(context option) on the name in the source) would go
    a long way to making __autos not needed.

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
    e.g. split off lower 32/16 bits, show decimal signed and unsigned interpretations (maybe ASCII character for lowest 8 bits).

