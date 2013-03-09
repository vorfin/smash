smash
------

`smash` **S**ends **M**ail **A**nd **S**tuff. **H**ippopotamus.



USAGE
-----

`smash` takes one or more arguments:

* An email address
* Zero or more files which contain your rules and messages

If no filenames are given, `smash` will try to read from `~/.smash`.


    # read two local files
    $ smash me@example.com /path/to/stuff.txt /path/to/other.txt

    # just read the default file
    $ smash me@example.com

    # you can mix local and remote files if you like
    $ smash me@example.com ~/.smash http://example.com/reminders.txt




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

Blank lines or lines beginning with `#` are ignored.



EXAMPLES
--------

Send a message only on a Wednesday:

    %a :: Wed :: New comics day!


To send on a Friday at 5PM:

    %a %H:%M :: Fri 17:00 :: Quitting time
