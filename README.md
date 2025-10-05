# BINCON

This is a simple python program that can take a CUE sheet file that references multiple
BIN files and merge all BIN files together to be more compatible with older software.

Unlike other BIN file merging utilities `bincon` modifies existing CUE data in place
and copies all existing lines rather than generating an all new CUE sheet. This
allows it to preserve any other metadata provided in the CUE sheet.

`bincon` does not merge BIN files across sessions however. The LEAD-IN and LEAD-OUT
areas may not have matching existing data and instead of zero padding a single file
to attempt to fill that space it makes more sense to leave sessions separate.
Multisession support is more common in modern software anyway.


## Help Info

        $ bincon -h
        usage: bincon [-h] [-d] [-o OUTPUT_FOLDER] ...

        BIN/CUE bin concatenation tool to combine multiple BIN files into one.

        positional arguments:
        filenames

        options:
        -h, --help            show this help message and exit
        -d, --debug           Only print CUE, don't write files
        -o OUTPUT_FOLDER, --output-folder OUTPUT_FOLDER
                                Path to output files to

        By Shelby Jueden


## Usage

`bincon` only has one useful optional parameter to specify an output folder.
Aside from that, you can pass the name of the CUE sheet to parse and a desired
output name for the new CUE and BIN files.

### Example

        bincon split-bin.cue new-bincue

This would read `split-bin.cue` as a source and generate `new-bincue.cue` and
`new-bincue.bin` files based on the data in the source.
