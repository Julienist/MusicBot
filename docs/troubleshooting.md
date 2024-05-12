---
title: Troubleshooting
description: "Common troubleshooting tasks for JMusicBot"
---

## Known issues
There may be bugs or temporary issues with MusicBot, such as tracks not loading from specific sources, like YouTube or SoundCloud. See the [Issues](https://github.com/jagrosh/MusicBot/issues) page and check if your issue is known.

## Problems starting the bot
!!! warning "A message stating 'A Java Exception has occurred' when I try to run the bot!"
* **Check your Java version** - You might be running a version of Java that is too old. JMusicBot reqires Java 11.

!!! warning "The .jar file is opening in WinRAR or is acting like a zipped file!"
* **Check your Java version** - You might not have Java installed
* **Set Java as the default program for .jar files** - On windows, you can do this by right-clicking the .jar file, select *Open with* > *Choose another app* > Check *Always use this app to open .jar files* > choose the newest Java installation

!!! warning "The bot is looking for the config file in an unexpected location!"
This can sometimes happen on Windows. Make sure:
* **Run the bot from a writable folder** - Use a folder in your 'Documents', not from your Desktop.
* **Double-Click**, don't use 'Open With'
* **Use Command Prompt or Powershell** in the folder with the jar and use `java -jar JMusicBot-VERSION_HERE.jar` (replacing the version correctly)

## Stopping JMusicBot as a process on Linux
In case of testing if your bot is working, but fails to work on Discord by using commands (see next paragraph).
You may want to stop JMusicBot, to reload your edited config.txt for example.
In case you ran the following command to launch the bot:
`java -Dnogui=true -jar JMusicBot-0.4.1.jar`
You can use the following command to search the process thats running JMusicBot on your linux system.
`pgrep -f JMusicBot`
a 4-digit number will roll out, this is the process ID.
`kill <process-ID-Number>`
will stop the bot from working.
*'<process-ID-Number>' is to be replaced with the given 4-digit number.

## Problems using commands
!!! warning "The bot doesn't respond to commands!"
* **Check the bot's prefix** - Look in your config file to see what you set the prefix to. The default prefix is a ping of the bot (ex: `@yourbot'sname ping` would run the ping command with the default prefix).
* **Check the bot's configured intents** - On the Discord Developer page, make sure that the 'Message Content Intent' is enabled. A message with a URL to your bot's specific developer page should be printed in console when starting up the bot.
* **Check the bot's permissions in Discord** - If the bot responds to the `help` command, but no other commands, the bot is likely missing Send Messages permissions in the text channel. If the bot can respond to `ping`, it has sufficient permissions to at least provide other error messages.

## Problems playing music
!!! warning "Music doesn't play if I set the volume to something other than 100!"
If music stops playing when you change the volume, this means that an internal library could not be loaded. This means you are either using an unsupported java version or the wrong jar file.
* **Check your Java version** - You might be running an unsupported version. Try re-installing the latest 64-bit version of java.

!!! warning "It seems like music is playing, but I don't hear anything!"
* **Check your Discord sound settings** - Make sure that you can hear other users, or other bots
* **Check that you don't have the bot muted** - You may have muted the bot, or set its User Volume to 0%

!!! warning "Music never starts playing!"
If the bot runs, but when you start to play music it never starts and is stuck at `0:00`, try some of these potential fixes:
* **Check your Java version** - You can run `java -version` at the command line to check your Java version. This bot requires JDK 1.8 or higher. OpenJDK _may_ work but is not guaranteed to provide full functionality. Also, for Windows user, make sure you are running 64-bit Java.
* **Check your hosting** - If you are hosting the bot on a VPS (Virtual Private Server), check which company is hosting it.
* **Check the logs** - There are a few things you can look for in the logs, but generally something like `Request Timed Out` means that the network connection that the bot has may be struggling and possibly unable to support streaming music.
* **Change your Discord voice region** - Discord frequently makes changes on their end which can cause issues and/or disconnects for JMusicBot. Try changing the region to see if that helps.

!!! warning "Error when loading from YouTube (429)"
If you see an error similar to "Error when loading from YouTube 429" when attempting to play songs from YouTube, it means that YouTube has blocked your bot's IP. Try one of these potential solutions, and see [here](https://github.com/jagrosh/MusicBot/issues/305) for more information:
* **Change IP addresses** - If you're hosting at home, you may be able to simply turn your router off and back on again. Some online hosts may offer the option to change your IP or to route through a different one.
* **Turn the bot off for several days** - Keeping the bot offline (or only playing songs from non-youtube sources) for several days will allow YouTube to eventually remove your IP ban.
