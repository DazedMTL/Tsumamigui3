# Apply Patch
1. Click Code
2. Click Download ZIP
3. Extract to game folder and Replace All.

# How To Contribute
TLDR 3 steps.

    Fork the repository.
    Make the changes.
    Submit a pull request to the project owner.

If everything looks good and doesn't break things I'll merge it in.

Longer Version:

Things that are needed:
* [VSCode](https://code.visualstudio.com/) Make sure you check all the boxes for context menus. ![image](https://github.com/DazedMTL/Dungeon-With-Girl/assets/96628874/7a84b624-32fe-4845-a0f6-2b9f39795070)
* The Game
* [Git](https://git-scm.com/downloads) (Use the default for everything. Just keep clicking Next)
* Motivation to learn

Installation:
1. Fork the repo using the fork button at the top. Click Code > HTTPS > Copy URL.
2. Right click on the game folder and click 'Open with VSCode' (Shift+Right_Click if you are on Windows 11)
3. Click on the Source Control Button and click initialize repository.

![image](https://github.com/DazedMTL/Dungeon-With-Girl/assets/96628874/61e818e6-11f9-450d-9d7d-263d109dbf56)

4. At the top click on Terminal > New Terminal. Enter the following: `git clone [URL_YOU_COPIED_ABOVE]`.
5. Copy the contents of the new folder created with git clone into the game folder and replace all.
6. Your source control menu should be good to go and look like this.

![image](https://github.com/DazedMTL/Dungeon-With-Girl/assets/96628874/c19787a0-172d-4a08-a37a-e3b56e70e86a)

Now you are all setup, all you need to do is play the game and look for any changes that need to be made. Stuff like spelling errors, wrong names, inconsistencies, spacing issues, etc.

7. Use the FIND functionality to search for what you are trying to fix. For example if a character's name is wrong, type that into the search menu and start looking, then make the change. Try not to mess with any scripts or variables you might see.

![image](https://github.com/DazedMTL/Dungeon-With-Girl/assets/96628874/589eccaf-7f86-43f7-a917-7e6e477b381a)

8. After you are satisfied with your changes it's time to put in a PR. Go to source control to see all your changes. Add a message and click the `Commit` button to save them all.

![image](https://github.com/DazedMTL/Dungeon-With-Girl/assets/96628874/a9a8973b-bc01-4184-bea9-63a925d961a2)

8. Click Sync to push your changes to your fork. Now all that's left is to put in a pull request.
9. Go to Pull Requests > New Pull Requests. Look at the arrow, your fork should be pointing to the original repo (mine). Add in details on what you fixed and Submit. If everything looks good I'll merge it in and you would have successfully contributed.

Got questions? Just shoot me a message, more than happy to walk you through any of the tools.'

Editing .ain files
------------------

There are two common usage patterns: one for editing text, and one for editing
code. In either case, you will have to enter commands at a command prompt
(e.g. cmd.exe) and edit some (rather large) text files.

In the following examples, I assume you have a file named "Rance10.ain" in the
current directory which you intend to edit.

### Editing Text

First, dump the text using the following command:

    alice ain dump -t -o out.txt Rance10.ain

This will create a file named "out.txt" containing all of the strings/messages
in the .ain file, sorted by function.

The syntax of this file is relatively simple. Anything following a ";"
character up until the end of a line is considered a comment and ignored when
the file is read back in. Initially all lines are commented out, meaning that
this file will cause no change to the output .ain file when given to ainedit.
To change a line of text, you must first remove the leading ";" character from
that line.

An uncommented line should contain one of the following forms:

    s[<number>] = "<text>"
    m[<number>] = "<text>"

The first form represents a string (text used by the game code) while the
second represents a message (text displayed to the player). Simply edit
`<text>` to change the text.

`<number>` is the ID of the string/message. You should not change this. It may
happen that the same string appears multiple times in the section of text you
are editing. It is only necessary to change the string once. If you set
different values for multiple instances of the same string, only the last
instance will be reflected in the output .ain file.

Once you've finished editing the text, you can reinsert it back into the ain
file by issuing the following command:

    alice ain edit -t out.txt -o out.ain Rance10.ain

This will create a file called "out.ain", which is a modified version of
"Rance10.ain" containing the modified text from the file "out.txt". You can
then replace the .ain file in your game directory with this file.

### Editing Code

First, dump the code with the following command:

    alice ain dump -c -o out.jam Rance10.ain

This will create a file named "out.jam" containing the disassembled bytecode
from the file "Rance10.ain".

A full tutorial on System 4 bytecode is outside the scope of this README.
Suffice to say, it's very low level and you probably don't want to make any
advanced mods using this method (but you're welcome to try). The syntax is
very close to what you'll see in the "Disassembled" and "Combined" views in
SomeLoliCatgirl's "AinDecompiler" tool.

Once you've finished editing out.jam, you can reinsert the code back into the
.ain file using the following command:

    alice ain edit -c out.jam -o out.ain Rance10.ain

This will create a file called "out.ain", which is a modified version of
"Rance10.ain" containing the modified code from the file "out.jam". You can
then replace the .ain file in your game directory with this file.

