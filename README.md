# VisiData

The Swiss Army Knife for Data Exploration

A console spreadsheet tool for discovering and arranging data

Great for immediate exploration of datasets to find out what is relevant and what isn't.
Usable via remote shell with Python3.
Download a 50kb standalone script onto a system with Python3 and start exploring within seconds.

## Features

- explore .csv, .json, .h5 files
- select and unselect rows by regex or python expression
- sort rows by one or more columns
- inner/outer/cross/diff join rows from multiple sheets by matching key columns
- aggregate rows by key columns, rollup functions (mean/min/max) provided for other columns
- instantly create derived sheets for frequency tables and column stats
- save any sheet arrangement as .csv/tsv, .json, or into .h5 table
- save layout for future instances
- custom sheet arrangements in Python3 scripts for repeated use on similar datasets that:
   - preprocess the data
   - coloring rows by matching regex or expression
   - \<Enter\> will 'dive' into cells by pushing a parameterized sheet onto the stack
   - add other actions
   - add computed columns
- all edits and transforms added to a changelog

- loads 100k row slices of larger datasets
    - slices are loaded on demand, so 100GB .csv files can be browsed instantly
    - same for remote datasets like bigquery/redshift or via sqlalchemy to RDBMS
    - background task has progress bar, can be interrupted

## Requirements
- Python 3.x
- h5py (if reading/writing HDF5 files)

## Usage

The 'g' prefix indicates 'global' context (e.g. apply action to *all* columns) for the next command only.

| Keybinding | Action | with 'g' prefix |
| ---: | --- | --- |
|   **F1** or **?**   | modal window with screen-specific keybindings | modal window with global keybindings |
|   **^R**     | reload this sheet from source (maintaining cursor position) | reload all sheets |
|   **^S**     | save current sheet to new file | save all sheets to new .h5 file |
|   **q**      | close current window/sheet | exit program (close all sheets) |
| **^C**        | cancel current long-running action |
|
|   **h**/**j**/**k**/**l** or **\<arrows\>** | move cell cursor left/down/up/right | move cursor all the way to the left/bottom/top/right |
| **PgDn**/**PgUp** | scroll sheet one page down/up (minus stickied rows/columns) |  go to first/last page |
|   **H**/**M**/**L**   | move cursor to top/middle/bottom of screen |
|   **J**/**K**     | skip down/up to next value in column |
|  **/**    | Search by regex or Python expression |
| **p**/**n**  | Go to previous/next search match | Go to first/last match |
| **^G**  | show sheet status line |
|
|**^H**/**^J**/**^K**/**^L** (or ctrl-arrows) | move current column or row one to the left/down/up/right (changes data ordering) | "throw" the column/row all the way to the left/bottom/top/right |
|    **{**/**}**    | Sort primarily by current column (asc/desc) |
|    **[**/**]**    | Toggle current column as additional sort key (asc/desc) |
|    **r**      | Remove all sort keys (does not change current ordering) |
|
|    **C**      | column arrangement screen.  Columns can be renamed, reordered, hidden/unhidden. shows stats (distinct/min/max/mean/stddev); whether pinned, in sort order, grouped by |
|    **-**      | Hide current column |
|    **_**      | Expand current column to fit all column values on screen |
|    **+**      | Expand all columns to fit all elements on screen |
|    **.**      | "pin" this column (make key column and sticky on the left)
|
|    **=**      | Add derivative column from expression |
|
| **ctrl-^**    | toggle to previous sheet |
|    **S**      | view current sheet stack | view list of all sheets |
|    **F**      | build frequency table for current column |
|    **E**      | view last full error (e.g. stack trace) |
|
|    **R**      | view select list for this sheet |
|    **\<Space\>**  | add current row to selected rows | select all rows |
|    \*/**u**   | select/unselect all rows | select/unselect across all sheets |
|    **\|**     | select by regex if this column matches | select row if any column matches |
|    **\\**     | unselect by regex or expression in this column | unselect row if any column matches | |
|    **,**      | select rows which match the current column value | select rows which have any column which matches the current column value |
| **v**/**V**   | hide/show unselected rows |
|
| **z**  | toggle group/ungroup by sequences in current column | group/ungroup by item in current column |


### Sheet list ('S')

| Keybinding | Action | with 'g' prefix |
| ---: | --- | --- |
| **&** | Inner Join of selected sheets. rows with unmatched keys are not present |
| **\*** | Full Join of selected sheets. all rows in both sheets are present |
| **\|** | Outer Join of selected sheets. all rows in first sheet are present; rows from other sheets with unmatched keys are not |


## References

[BurntSushi/gxd]
[sc]
[teapot]