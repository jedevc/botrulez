# Botrulez

These guidelines exist as a standard for which bots should obey to be
consitent with each other. The goal of a bot is to enhance the experience
of the user and one of the ways to do this is to provide a unified interface
between bots.

Note that all bots do not have to obey these standards. There are sometimes
very good reasons as to why a bot may not be able to implement the following
commands. However, it is **strongly** recommended that you do so.

***

# Commands

Bots should preferably not reply to comments unannounced. The user of the bot
should be able to predict when the bot will appear. The preferred way for
this is to use commands.

A command is a statement beinning with a '!' with the command name with possibly
arguments following. They should match this regex - /^!\S+(\s+\S+)*$/.

***

## Standard commands

### !ping
When a '!ping' is sounded, the bot should reply with a 'Pong!'.
Other replies are permitted - however they should be concise and predictable.

There are 2 types of ping - general and specific.

In a general ping, every bot should reply with its response whereas in a
specific ping, only the bot that is specified in the command should reply.

General syntax:

    !ping
Specific syntax:

    !ping @BotName

Each bot is strongly recommended to respond to the general ping, however, the
bot is not required to respond to the specific ping.

### !help
When a help request is made using '!help' then the bot should resond with a help
text detailing the purpose of the bot and how to use it.

As with pings, there are two variations on the command.

With a general help request, each bot should reply with a concise description of
the purpose of the bot. A specific help request reply should contain a more
detailed description of the bot and a list of all the commands that a bot will
reply to and how to use them.

General syntax:

    !help
Specific syntax:

    !help @BotName

### !uptime
When an '!uptime' command is given, then the bot specified should reply with the
amount of time it has been active and online without crashing and the time that
the bot became active. 

The time should be formatted as such with the most significant time measurement
appearing first.

The ideal response would look like this:

    BotName: /me has been up since 2015-08-08 16:09:50 UTC and has been up for
    2d 3h 0m 4s.

Syntax:

    !uptime @BotName

***

## Non-standard commands

In some cases bots may be forced to respond to these commands by the platform or
the programmer may with to implement them as a way to give the user further
control over the bot.

### !pause and !restore
When the '!pause' command is given to a bot, then the bot should cease all it's
activity but continue to remain in the nick list. When the '!restore' commmand
is given to a paused bot, then the bot should continue to perform it's duties.
The uptime should then be restarted at this point.

Syntax:

    !pause @BotName
    !restore @BotName

### !kill
Sometimes the bot will go out of control and the user may find it neccessary to
terminate it. When the '!kill' command is given the bot will cease to exist
immediately. It will exit the room and not appear again even if called for.

Syntax:

    !kill @BotName

### !restart
If the '!restart' command is given to a bot, then it should restart all of it's
processes, and appear again. This may be helpful in a bot that is not yet bug
free and requires occasional restarts to fix it. After this command, the uptime
should be restarted.

Syntax:

    !restart @BotName
