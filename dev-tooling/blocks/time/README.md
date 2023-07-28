# Time

The Time category of Blocks in the GraphLinq IDE focuses on obtaining time and date information and performing manipulations with timestamps. A timestamp serves as a unique label representing a specific moment in time, capturing the date and time when a particular event occurred or when data was created or modified.

GraphLinq utilizes Unix Timestamps to generate current time and date values. Unix timestamps count the number of seconds that have passed since a predefined reference point, known as the "Unix epoch," which is set at January 1, 1970, 00:00:00 UTC (Coordinated Universal Time).

Blocks for Generating Timestamps:

* The [Get Timestamp](get-timestamp.md) block provides the current Unix timestamp, indicating the present date and time.
* The [Get Millisecond Timestamp](get-milliseconds-timestamp.md) block is similar but includes milliseconds for greater precision in the timestamp.

Subtracting Time from Timestamps:

* To subtract time from the current timestamp, the [Get Timestamp Offset](get-timestamp-offset.md) block allows users to specify the desired time interval to deduct.
* The [Get Milliseconds Timestamp Offset](get-milliseconds-timestamp-offset.md) block performs the same operation but with milliseconds.

Formatting Timestamps:

* To convert a Unix timestamp into a human-readable date format, the [Format Date](format-date.md) block is utilized. Users can customize the date format as desired.
* The [Timestamp to Date](timestamp-to-date.md) block serves a similar purpose, enabling the conversion of Unix timestamps to human-readable date formats.
* The [Millisecond Timestamp to Date](millisecond-timestamp-to-date.md) block performs the same operation but includes milliseconds for precision.

Additional Time Blocks:

* The [Execution Time Interval](execution-time-interval.md) block calculates the time interval between the start and end of executing a specific part of the graph.
* The [Timer](timer.md) block can be used to trigger an event after a specified time interval, facilitating time-based operations.

These time-related blocks provide developers with the tools to work with timestamps, manipulate time and date data, and convert between Unix timestamps and human-readable formats, streamlining time-related operations in their graphs.
