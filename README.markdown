julian
------

`julian` is a script that sends you some mail every so often.



USAGE
-----

`julian` takes at most two arguments: an email address and,
optionally, a file which contain your rules and messages.

    $ julian me@example.com /path/to/stuff.txt


If a filename is not given, `julian` will try to read from
`~/.julian`.


You can also pass a remote file, if that's your thing:

    $ julian me@example.com http://example.com/reminders.txt



FILE FORMAT
-----------

The format for the rules file is dead simple. Each line should contain
three or four fields, separated by a double colon:

    <date_format> :: <date_value> :: <subject> :: <body>

1. A `strftime`-formatted string.
2. The value the previously mentioned field match
3. The message subject
4. The message body

The message body is optional and if not provided, the message subject
will act as the body.

Blank lines or lines beginning with '#' are ignored.



EXAMPLES
--------

Send a message only on a Wednesday:

    %a :: Wed :: New comics day!


To send on a Friday at 5PM:

    %a %H:%M :: Fri 17:00 :: Quitting time
