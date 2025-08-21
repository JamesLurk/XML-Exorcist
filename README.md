# XML-Exorcist
When converting XML files using Gibbed Tools, it's common to encounter generic errors indicating invalid XML without specifying which file contains the problem or the exact line of the error. This becomes especially challengingg when working with many files simultaneously.

The provided PowerShell script automates the validation of multiple XML files in a directory, identifying not only which files have errors but also displaying detailed error messages, including the exact line and position where the problem occurs. This greatly facilitates locating and fixing errors prior to conversion, saving time and avoiding frustration.

Moreover, the script captures different XML exception types, providing clear and distinct messages for XML syntax errors and other unexpected issues, giving a more precise insight into what is wrong.

This approach is essential for any modder or developer working with large amounts of XML files, ensuring a much more stable and efficient editing and conversion pipeline.

--- How to use the script to find XML errors for Gibbed Tools

Open the folder where your .xml files are.

Hold Shift and right-click inside the folder (on a blank space).

Select “Open PowerShell window here”.

Paste the script I gave you.

Press Enter and wait for it to check all files.

The script will tell you which files are OK and which have errors — including the exact line number where the problem is.

The previous version of the script took 1 minute and 37 seconds to scan a directory containing 5,030 XML files.
With the latest optimizations, the same operation now completes in just 21 seconds — a 4x speed boost.
This improvement comes from multiple core-level enhancements (see table below), designed to handle massive XML libraries with minimal resource usage

New Features:
Automatic Logging to File
•    Every console output is now also written to a file:
scan_results.log

•    This log includes all lines, with timestamps and colors preserved (where supported).
•    Makes it easy to:
o    Review results later
o    Share logs with others
o    Avoid losing console output due to scroll limits

No More Lost Output
•    PowerShell consoles have a scrollback limit — when scanning thousands of files, older messages disappear.
•    With the new log file, you never lose anything, no matter how long the scan runs

Performance Optimizations

Hashtable lookup  - Instant O(1) lookup time per hidKey – extremely fast even with 10k+ files lol
Get-Content -Raw - Reads entire file in one go – much faster for XML parsing
Logging function  - Writes console output to a log file simultaneously
Colored output - Console feedback is color-coded for easy visual identification
Trims fields - Prevents false mismatches caused by invisible trailing whitespace
Minimal memory  - Doesn’t store unnecessary objects or entire XML structures

Tip: Increasing Console Scrollback Limit
For those who still prefer reading results in the PowerShell window:
You can manually increase the scrollback buffer:
Right-click the top of the PowerShell window → Properties
Go to the Layout tab
Set the Screen Buffer Size - Height to 9999 (or even more)
Click OK and restart PowerShell
This allows you to scroll back through thousands of lines before they disappear.... though i still recommend using the .log file for large scans.
