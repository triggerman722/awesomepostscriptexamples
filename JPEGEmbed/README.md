## JPEGEmbed

OH MY GOD!!!! What a pain it was to figure out how to embed the contents of a JPEG file inside a postscript file. This activity, although pretty much a waste of time today, is still something that has some distant value, as by controlling the postscript file, you can create documents to your extremely exacting specifications.

Finally I found this:
http://wwwimages.adobe.com/content/dam/Adobe/en/devnet/postscript/pdfs/5116.DCT_Filter.pdf
and for a change, a useful example was provided!

Before you embed the JPEG, you need to know its width and height.
- From the terminal, type `identify <nameofjpg.jpg>`
- Make a note of the width and height
- Using nano, edit this file and replace the value 1400 with the width of your file
- Same story, replace 365 with your height. Careful: width appears twice, and height three times.
- You can keep, edit or get rid of the line that reads `126 270 translate`. Translate sets the starting point for displaying the image.
- You should know that in postscript, 0, 0 refers to the bottom left corner, and increasing the Y value moves UP...this is different than most systems
- If you leave out the X Y translate line, the image will be printed below the bottom of the page (ie. invisible). So at a minimum, you should provide a positive Y value.
- Same thing, keep, edit or delete `349 252 scale`, but apparently some sort of scaling is necessary, so you may want to just replace the values with the width and height of your image.
- Using nano, move your cursor one character (exactly) after where it reads `exec` on the last line of the file PRE-JPEGEmbedded.ps
- Press <kbd>CTRL</kbd>+<kbd>R</kbd>
- type in the name of the JPEG to include, the press <kbd>ENTER</kbd>
- Press <kbd>CTRL</kbd>+<kbd>X</kbd> to save and exit.
- From the terminal, type `ps2pdf PRE-JPEGEmbedded.ps Results.pdf`
- With any luck, it will work!
