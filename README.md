# Botrulez

These guidelines exist as a standard which bots should obey to be consistent
with each other. The goal of a bot is to enhance the experience of the user
and one of the ways to do so is to provide a unified interface across bots.
These standards are all about improving the user experience of bots; if you
believe that breaking some of them would improve the bot, you may go ahead —
rules are meant to be broken (if you know what you're doing).

***

# Commands

The user of the bot should be able to predict when the bot will appear. This
helps avoid "spammy" bots. Therefore, bots should mostly be interacted with
using commands. 

A command is a statement beinning with a `!`, immediately followed by the
command name, with arguments possibly following. Therefore, a command would
match the regex `/^!(\S+)(\s+(\S+))*\s*$/`, where the first grouping contains
the command name, and the third one the individual arguments.

***

## Standard commands

This section specifies some commands of use for a large majority of bots.

### !ping
When a `!ping` is sounded, the bot should reply with a `Pong!`. Other replies
are permitted, however, they should be concise and predictable.

There are 2 types of ping — *general* and *specific*.

In a general ping, every bot should reply with its response, whereas in a
specific ping, only the bot that is specified in the command should reply.

**General syntax:**

    !ping

**Specific syntax:**

    !ping @BotName

### !help
When a help request is made using `!help`, the bot should resond with a help
text detailing the purpose of the bot and how to use it.

As with pings, there are two variations on the command.

To a general help request each bot should reply with a concise description of
the purpose of the bot. A specific help request reply should contain a more
detailed description of the bot and a list of all the commands that a bot
will reply to and how to use them.

**General syntax:**

    !help

**Specific syntax:**

    !help @BotName

### !uptime
When an `!uptime` command is given, the bot specified should reply with the
amount of time it has been active and online without crashing and the time
when the bot became active. While the two pieces of information are
redundant, they are both equally useful for human users.

The time should be formatted with the most significant time measurement
appearing first, as [ISO 8601](http://xkcd.com/1179/) specifies.

The ideal response would look like this — more or less detail may be added
at wish (although the reply should be still useful) —:

    BotName: /me is up since 2015-08-08 16:09:50 UTC (2d 3h 4s)

**General syntax:**

Differently to the other commands, a general reply is not mandated (why would
one want to know all the bots' uptime?); apart from that, the syntax is
similar:

    !uptime

**Specific syntax:**

    !uptime @BotName

***

## Non-standard commands

In some cases bots may be forced to respond to these commands by the platform,
or the programmer may wish to implement them as a way to give the end-user
further control over the bot.

### !pause and !restore
When the `!pause` command is issued to a bot, then the bot should cease all
of its activity but continue to remain in the nick list. When the `!restore`
commmand is given to a paused bot, the bot should continue performing its
duties again; the uptime should be restarted at this point.

**Syntax:**

    !pause @BotName

    !restore @BotName

### !kill
Sometimes, a bot might go out of control and the user may find it neccessary
to terminate it. When the `!kill` command is given the bot shall cease to
exist immediately; it shall exit the room and not appear again even if called
for.

If you — as an end-user — find it neccessary to kill a bot that does not
belong to you, please explain to the creator of the bot your problems with it
to enable them to fix it.

**Syntax:**

    !kill @BotName

### !restart
If the `!restart` command is given to a bot, the bot should restart all of
its activities, and appear again. This may be helpful in a bot that is not
bug free and requires occasional restarts to fix issues. After this command,
the uptime should be restarted.

**Syntax:**

    !restart @BotName

### !conjure
Some bots do perform an idiomatical action under certain conditions (like,
a *@tumbleweed* bot would "roll by" if the room is silent for a long time);
to let the bot perform the action unconditionally, the `!conjure` command
may be used.

**Syntax:**

    !conjure @BotName

***
