I wanted to see if it was possible to run vim in ubuntu itself. 
At first I was very confused, since it took me some time to figure out what the prof. in the video lectures provided is doing.

So I searched it up and apparently something called `vim-tiny` comes pre-installed with ubuntu.

but if you need the full version with additional features, you can install it using:
`sudo apt update
sudo apt install vim`

which I did.
and also learned about the basic commands! and ran a simple hello world program

`vi hello.c`

`gcc -o hello hello.c` //to compile. I had to install gcc asw lol

`./hello` //to run it

1. **Opening a File**:
   - Both: `vi filename` or `vim filename`

2. **Saving and Exiting**:
   - **`:w`** – Save changes
   - **`:q`** – Quit without saving
   - **`:wq`** or **`:x`** – Save and quit
   - **`:q!`** – Quit without saving (discard changes)

3. **Basic Navigation**:
   - **`h`** – Move left
   - **`j`** – Move down
   - **`k`** – Move up
   - **`l`** – Move right
   - **`gg`** – Go to the start of the file
   - **`G`** – Go to the end of the file

4. **Editing Text**:
   - **`i`** – Enter insert mode (type text)
   - **`Esc`** – Return to command mode
   - **`dd`** – Delete an entire line
   - **`x`** – Delete a single character
   - **`u`** – Undo the last action
   - **`Ctrl + r`** – Redo (only available in `vim`)

5. **Advanced Navigation in `vim`**:
   - **`Ctrl + o`** – Jump back to the previous position
   - **`Ctrl + i`** – Jump forward to the next position
   - **`%`** – Jump to the matching parenthesis, brace, or bracket (helpful for code)

6. **Search**:
   - Both: **`/text`** – Search for `text` in the file
   - **`n`** – Move to the next occurrence
   - **`N`** – Move to the previous occurrence

7. **Copy, Cut, and Paste**:
   - **`yy`** – Copy a line
   - **`dd`** – Cut a line
   - **`p`** – Paste below the current line
   - **`P`** – Paste above the current line

8. **Visual Mode** (Only in `vim`):
   - **`v`** – Start visual mode to select characters
   - **`V`** – Start visual line mode to select entire lines
   - **`Ctrl + v`** – Start visual block mode for column selection

9. **Syntax Highlighting (Only in `vim`)**:
   - **`:syntax on`** – Enable syntax highlighting
   - **`:syntax off`** – Disable syntax highlighting
