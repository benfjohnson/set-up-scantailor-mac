# Set up scantailor on macOS

1. Clone Tulon's scantailor fork on your local machine:

   `git clone https://github.com/Tulon/scantailor.git`

2. `cd` into the repo, and switch to the experimental branch:

   `git checkout experimental`

3. Use [homebrew](https://brew.sh/) to install all dependencies:

   `brew install qt5 boost cmake eigen jpeg`

4. Run cmake at the root of the scantailor directory, passing in the `CMAKE_PREFIX_PATH` (yours may be slightly different):

   `cmake . -DCMAKE_PREFIX_PATH=/usr/local/Cellar/qt/5.9.1`

   You should see several success messages after this command finishes running.

6. Run `make`

7. Run `sudo make install`

At this point, you should have `scantailor` installed! If you run `scantailor` from your terminal and the GUI launches, that's a good sign. Next we'll run it against an image.

8. Download or move one or more scanned document images into an 'input' folder in your location of choice. Create an 'output' folder in that same location.

9. Run the following command (if an insufficient number of options aren't provided to the cli, the command will succeed but no output will be generated):

   ```
   scantailor-cli -v --margins=0 --layout=1 --deskew=auto --content-detection=normal --alignment-vertical=bottom --alignment-horizontal=center --white-margins=true --color-mode=black_and_white --dpi=600 --output-dpi=600 --despeckle=off --tiff-compression=lzw --start-filter=1 --end-filter=6 input output
   ```

Now, each of your input images should have a corresponding .tif file in the output directory, which has enhanced (straightened, brightened, etc.).

Credits: Much of these instructions were gathered from [this forum discussion](https://forum.diybookscanner.org/viewtopic.php?f=21&t=3407)


