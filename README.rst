Inbox.py: SMTP Server for Humans
================================

This is the simplest SMTP server you'll ever see. It's asynchronous. 

One instance should handle over one thousand emails per second.

This version adds flanker https://github.com/mailgun/flanker message 
parsing and returns msg to handle so it's easier to create a proxy and
manipulate original message.

Original return values are kept ``` def handle(to, sender, subject, body, ``` for compatibility.

Usage
-----

Give your app an inbox easily::

    from inbox import Inbox

    inbox = Inbox()

    @inbox.collate
    def handle(to, sender, subject, body, msg):
        ...

    # Bind directly.
    inbox.serve(address='0.0.0.0', port=4467)


You can also defer to the commandline::

    if __name__ == '__main__':
        inbox.dispatch()

::

    $ dasinbox.py 0.0.0.0 4467
    [2012-04-28 07:31] INFO: inbox: Starting SMTP server at 0.0.0.0:4467


Installation
------------

Installing Inbox.py is simple::

    $ pip install inbox
