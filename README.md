Priorities:
*   (0)   showstopper [none hit so far, phew :-)]
*   (1)   important
*   (nth) "nice to have"
*   (use) usability & enjoyment maximization
*   (cos) cosmetics, eye candy

# General for all debug views (e.g. Modules, Threads, Call Stack):

* (1) as a minimum of interactivity, all text in the tables in these views should be exportable (copy-able) to the clipboard
        Maybe with one click for the whole text as a tab-separated/comma-separated text table and optionally also for a single table cell.
        partial selection & copy is nice but lower priority
        Note: This allows the user to use searching features, analysis features in other applications quickly as long
              as they are not provided by remedybg itself. Single-cell copy will be very useful with calculators like speedcrunch.
        Examples: The Modules view is almost unusable without such features.

* (use) for table cells which are only shown partially, show the full cell contents if possible on mouse over in
       the status line or in a separate full-width line at the bottom of the window, a line which can be disabled for people
       optimizing vertical screen space
       Note: I think I'd like this better than showing text in pop-ups / "tooltips" as is down now for the EFLAGS register.
             A dedicated line for such mouse-over text would minimize distraction of the user.
             Also importantly: Such a separate mouse-over-line could work nicely while stepping if one leaves the mouse
             hovering over the same spot. Motto: Left hand/keyboard for stepping, right hand/mouse for inspection, similar to how it
             is done in games.

# General tabbed views
* (use) I always find that having the closing "X" on every tab causes usability issues. When one flicks quickly
  through the tabs it is too easy to close one accidentally, which is annoying. I'd prefer having a "Close"
  option on a right-click context menu on the tab. (It is also Huffman coding: closing is much rarer than switching tabs.)

# General menus
* (cos) for the selected menu option, the contrast is very bad for the hotkey text to the right of the option.
    Would be nice to make it white on light blue or so.

# Session menu
* (use, nth) tab completion for filenames in target, directory, and argument boxes

# Image and symbol loading
* (use) give error message if the image is used incrementally in therefore does not work in remedybg (do not fail silently)

# Process control
* (use) When the process exits, there should be a notice in the status bar (best: green for exit status 0, red for != 0)
               Currently it can be confusing for the user if the process exits and the "Output" tab is not visible.
               Also, remedybg is so blazingly fast, that sometimes one does not even notice that it has already reacted to F5
               and executed the whole process to completion :-).

# Watching variables
* (1) faster way to add watched expressions that occur in the source
      Ideas: single-word expressions could be added by double-clicking
             text selection and right-click>(context option) or a hotkey would work even for more complicated expressions
* (1) array inspection within structs and in "__locals"
* (use) make it more obvious that one can add new items by clicking below the last watch item; use all space below the last item as clicking area for this
* (use) allow expanding/collapsing of watched structs e.g. by double-click to increase the attack area for collapsing/expanding
     Note: For the root item, this currently collides with the edit-on-double-click. Maybe it would be fine
           to toggle expansion along with the editing? After all, what I want to edit, I usually also want to see, right?
           A click on the collapse item could then re-collapse and also quit the editing, which seems useful.
* (nth) "__autos" struct which works similar to Visual Studio "Autos" watch window (shows variables used around the current source line and return values of recently returned functions)
     Note: The __autos features can be rather nice but if it introduces a lot of complexity, I'd be fine without it.
           Adding a very quick way to add watches (like double-click or right-click>(context option) on the name in the source) would go
           a long way to making __autos not needed.

# Disassembly view
* (1) this view desperately needs navigation. minimum: go to address/symbol.
* (cos) -> (use) Use (maybe only slightly) different colors for address, machine code bytes, disassembly, respectively.
             Note: This becomes a usability feature in cases where the machine code bytes "bleed" into the disassemble column.

# Register view
* (use) color changed register values after stepping
* (use) offer "add to watch" context menu to make it more obvious that that is (already) possible
* (use) on mouse-over on a register, show multiple interpretations of the register bits in the mouse-over-text-line discussed above
    e.g. split off lower 32/16 bits, show decimal signed and unsigned interpretations (maybe characters for lowest 8 bits)

