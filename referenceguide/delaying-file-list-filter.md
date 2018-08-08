
Delays the filtering process for the specified amount of time.
File list filter that delays the filtering process for the specified amount of time.

In certain fringe cases this filter could be useful. For example when the file name or modified time cannot be used to determine whether a file is still being written to, this filter could add a delay to give processes the time to finish writing to the file.


Delay
The time in milliseconds to delay the filtering process.

Default is <code>5000</code> (5 seconds).

