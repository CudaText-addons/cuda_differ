Differ plugin for CudaText

Compares two files side-by-side in a single tab, highlights all differences,
and lets you edit the files directly in the compare view -- your changes are
synced back to the original files automatically.


== What it does ==

- Opens two files (or two untitled tabs) in one split tab and highlights
  added, deleted, and changed lines side-by-side.
- Lets you edit either side of the compare view. When you save, your edits
  are written back to the original files on disk -- no need to copy text
  around manually.
- Keeps the original tabs open while you compare, so you always have both
  the originals and the compare view available.
- Remembers your compare tabs across CudaText restarts. If you close
  CudaText with a compare tab open, it is restored when you start again.
- Provides synchronized scrolling so both sides stay aligned as you
  navigate.


== Commands ==

All commands are in the "Plugins / Differ" menu.

Choose files...
    Opens a dialog to pick two files to compare. The dialog suggests
    recently used files and files currently open in CudaText.

Compare current document with file...
    Compares the file in the active tab with another file you pick from
    a dialog.

Compare current document with tab...
    Compares the file in the active tab with another open tab.

Diff current document with file...
    Produces a unified diff (patch-style) of the active file and a file
    you pick. The result opens in a new read-only tab.

Diff current document with tab...
    Same as above, but compares with another open tab.

Refresh
    Re-runs the comparison after you edit either side. Useful if
    auto-refresh is off.

Focus the opposite file
    Moves the cursor to the other side of the split.

Select current difference
    Selects the difference block under the cursor.

Select all differences
    Selects all difference blocks in both files.

Jump to next difference
    Moves the cursor to the next changed block.

Jump to previous difference
    Moves the cursor to the previous changed block.

Copy current difference to the right
    Copies the selected difference from the left file to the right file.

Copy current difference to the left
    Copies the selected difference from the right file to the left file.

Copy current line to the right
    Copies the line under the cursor from the left file to the right file.

Copy current line to the left
    Copies the line under the cursor from the right file to the left file.

Move 2 comparing files to separate tabs
    Closes the compare tab and returns the two files to separate tabs.

Config...
    Opens the options dialog.

Clear recents history
    Clears the list of recently compared files shown in the "Choose files"
    dialog.


== Tab context menu ==

Right-clicking a tab title shows "Differ" submenu with:
- Compare with... -- pick a file to compare against this tab
- Compare with focused tab -- compare this tab with the currently focused tab
- Compare with tab -- compare this tab with another open tab
- Back to separate tabs -- return from compare view to two separate tabs


== Saving and syncing changes ==

When you edit files inside the compare view and press Ctrl+S:

- Both sides of the compare are saved at once -- you only need to save
  one side, the other is saved automatically.
- Your edits are written back to the original files on disk immediately,
  so the files on disk reflect your changes.
- If an original was an untitled tab (no file on disk), it is marked as
  modified (dot on the tab) but no Save dialog appears. You can save it
  later if you want.
- Undo/Redo history is preserved in the original tabs, so you can undo
  the synced changes with Ctrl+Z after switching to the original tab.


== Compare tabs and restarts ==

Compare tabs survive CudaText restarts:

- If you close CudaText with a compare tab open, the compare tab is
  restored when you start CudaText again, with the same files and the
  same comparison.
- The plugin loads automatically on startup only when compare tabs are
  active, so there is no performance impact when you are not comparing.
- When you close the last compare tab, the plugin stops auto-loading on
  the next startup.

When you close a compare tab manually (not via app exit):
- If you have unsaved changes, CudaText asks whether to save or discard.
- If you save, your changes are synced to the original files.
- If you discard, the temp files are deleted and the originals keep
  their last-saved content.
- If you cancel, nothing happens -- the compare tab stays open and
  fully functional.


== Command-line support ==

You can start a comparison from the command line:

    cudatext -p=cuda_differ#filename1#filename2

This launches CudaText with the two given files opened in the Differ plugin.


== Options ==

Open the options dialog via "Options / Settings-plugins / Differ / Config"
or "Plugins / Differ / Config...".

Available options include:
- Colors for changed, added, and deleted lines
- Color of the inter-line gap background
- Synchronized scrolling (vertical/horizontal) toggle
- Auto-refresh on edits
- Sync caret between the two sides
- Number of context lines in unified diff output
- Detail comparison of changed lines (character-level highlights)
- Maximum number of recent files in the "Choose files" dialog
- Maximum number of recently opened files kept in history.json


== Notes ==

- Untitled tabs can be compared just like saved files. A temporary copy
  is made for the compare view, and your edits are synced back to the
  original untitled tab when you save.
- If both files become identical after editing, all markers are cleared
  and a message is shown.


== Authors ==

  OlehL, https://github.com/OlehL
  Alexey Torgashin (CudaText)
  Andrey Kvichanskiy, https://github.com/kvichans
  Vivalzar, https://github.com/Vivalzar
  Bzdr Elmers, https://github.com/badrelmers

License: MIT
