# Time

This category of Blocks deals with getting time/date and manipulating those values. A timestamp is a sequence of characters or encoded information that represents the date and time at which a particular event occurred or a specific piece of data was created or modified. In simpler terms, a timestamp is a way of labeling a specific moment in time.

GraphLinq uses Unix Timestamps to generate the current time/date. Unix timestamps work by counting the number of seconds that have elapsed since a specific moment in time, which is defined as January 1, 1970, at 00:00:00 UTC (Coordinated Universal Time). This moment is known as the "Unix epoch".

There are two blocks for generating a timestamp:  [`Get Timestamp`](get-timestamp.md) [`Get Millisecond Timestamp`](get-milliseconds-timestamp.md). If you would like to subtract time from the current timestamp you can use `G`[`et Timestamp Offset`](get-timestamp-offset.md)  and [`Get Milliseconds Timestamp Offset`](get-milliseconds-timestamp-offset.md) respectively.

To format a timestamp into a human readable date the blocks are [`Format Date`](format-date.md) ,  [`Timestamp to Date`](timestamp-to-date.md) , [`Millisecond Timestamp to Date`](millisecond-timestamp-to-date.md) .

The time category has two additional blocks: [Execution Time Interval](execution-time-interval.md), and [`Timer`](timer.md).
