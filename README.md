# Livestream wrapper

A wrapper for livestreamer, written as a bash script.

## Dependencies
- livestreamer
- GNU Parallel

#### NOTE:

As the wrapper has yet to transfer other arguments to livestreamer, make sure that livestreamer's config file has been set up
to ensure that custom options such as authenticator tokens and video players have been set.

## Aliases:

Adds alias functionality for oftenly used URLs. Aliases are stored and can be added, removed, and overwritten.
Aliases for URLs makes using livestreamer easier and removes the need to remember various URLs.

Aliases are stored in the same directory as the livestreamer config file:
```
/home/$USER/.config/livestreamer/
```

#### Adding aliases:

Aliases are case-sensitive and must be unique and not contain special characters (alphanumeric only).

Aliases must not have the same name as commands.

To add an alias, use the command:
```
livestream add ALIAS URL
```

Aliases can also be added by modifying the file within the config folder.

In the case of an alias name conflict, an option to overwrite the existing URL is given.

#### Removing aliases

Removing aliases is done by the command:
```
livestream remove ALIAS
```

URLs can also removed along with all associated aliases:
```
livestream remove URL
```

 Aliases can also be removed by modifying the file within the config folder.
 
#### Using aliases (playing streams)

Aliases are shorthand for URLs, thus take the place of any working URL for livestreamer.
```
livestream ALIAS QUALITY  == livestream URL QUALITY
```
The given order must be followed.

If no QUALITY argument is supplied, then quality defaults to best.

#### Listing aliases

Aliases are listed using the commmand:
```
livestream list
```

## Pinging

Pinging displays whether a channel is online or offline. 

Pinging with an alias or URL argument will display the channel's status:
```
livestream ping URL
livestream ping ALIAS
```

Pinging without an argument will display the status of all aliased channels:
```
livestream ping
```

Pinging is slow, especially if pinging all aliased channels as it is done so concurrently.

## TODO:
  - Transfer all arguments beyond $channel and $quality to livestreamer
  - Display titles of online channels
    - Can't be done with only livestreamer, need another tool
  - Add commands to reorder alias list (low priority)
  - Checking channel status may need to be fixed if found unreliable
  - Add tags to aliases (website, genre, game, etc.)
  	- livestream tag CHANNEL TAG
	- livestream untag CHANNEL TAG
	- livestream untag CHANNEL *
  	- Use tags to list, ping
  - Prioritize listing ONLINE channels on top when pinging
  - Strengthen alpha-num alias requirements
