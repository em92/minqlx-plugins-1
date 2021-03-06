# minqlx-plugins by iouonegirl

This repo will contain several plugins which I have developed for [Mino's minqlx](https://github.com/MinoMino/minqlx "MinoMino/minqlx").

Most ideas have been created, worked out and evaluated on <http://station.boards.net>, the official forum of the 'Bus Station' servers.

Feel free to change variables and output messages in the files themselves, but this could introduce bugs if you don't really know what you're doing. As with most software, my plugins are not 100% foolproof and occasional unexpected behavior can occur. 
If you would notice any unusual behavior resulting from an 'iouplugin' on your server, please contact me about it. 
This also goes for any advice or crazy ideas for new plugins anyone might have.
My email address can be found on github, and I can usually be found on the [Quakenet IRC](http://webchat.quakenet.org/?channels=minqlbot) channels #busstation, #iouonegirl, #minqlbot, #qldedsrv.

If you wish to donate, please find a little paragraph and paypal link [below](https://github.com/dsverdlo/minqlx-plugins#donate).
# Plugin list:
| Name | Short Description | Raw |
| ---- | :---------------: | :-- |
[`afk`](https://github.com/dsverdlo/minqlx-plugins#afk)|Detect AFK people and place them in spectator (after a warning).|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/afk.py)
[`anti-rape`](https://github.com/dsverdlo/minqlx-plugins#anti-rape)|In round-based game modes; apply calculated handicaps to people playing above the server average|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/anti_rape.py)
[`autospec`](https://github.com/dsverdlo/minqlx-plugins#autospec)|If CA or FT teams are uneven, make the last person spec.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/autospec.py)
[`centerprint`](https://github.com/dsverdlo/minqlx-plugins#centerprint)|Provides easy way to broadcast messages on peoples screens, and provides a "last enemy standing" toggle.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/centerprint.py)
[`disable_votes`](https://github.com/dsverdlo/minqlx-plugins#disable_votes)|Disable the ability to make certain callvotes during a game.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/disable_votes.py)
[`gauntonly`](https://github.com/dsverdlo/minqlx-plugins#gauntonly)|When 1 last standing person faces a lot of enemies, start gauntonly mode.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/gauntonly.py)
[`funlimit`](https://github.com/dsverdlo/minqlx-plugins#funlimit)|Automatically disables fun(.py) sounds during a match/rounds.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/funlimit.py)
[`intermission`](https://github.com/dsverdlo/minqlx-plugins#intermission)|Play 1 song out of a list after every match end.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/intermission.py)
[`mybalance`](https://github.com/dsverdlo/minqlx-plugins#mybalance)|Elo-limits, warmup reminders, team balancing for CA,TDM,CTF,FT.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/mybalance.py)
[`myban`](https://github.com/dsverdlo/minqlx-plugins#myban)|Use the !ban command with a player's name instead of ID.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/myban.py)
[`myessentials`](https://github.com/dsverdlo/minqlx-plugins#myessentials)|Use names with the essential commands, like !red iou, !mute iou, !kick iou, ...|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/myessentials.py)
[`myirc`](https://github.com/dsverdlo/minqlx-plugins#myirc)|Supports broadcasting to keyed(passworded) channels, shows more colors, and broadcasts live updates to the topic.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/myirc.py)
[`player_info`](https://github.com/dsverdlo/minqlx-plugins#player_info)|Display some player information. Maybe upon player connect if you want.(Also gives a warning or a ban for deactivated qlstats accounts)|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/player_info.py)
[`railable`](https://github.com/dsverdlo/minqlx-plugins#railable)|Toggle to get a 'railable' message when your health drops too low.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/railable.py)
[`translate`](https://github.com/dsverdlo/minqlx-plugins#translate)|Look up normal and urban definitions, translate works and sentences, translate last 3 things someone said.|[`raw`](https://raw.githubusercontent.com/dsverdlo/minqlx-plugins/master/translate.py)



# **afk**
- Detects players who are not moving and will slap them until they die and then puts them to spectator.
- CVARS
  -  qlx_afk_warning_seconds "10"
  -  qlx_afk_detection_seconds "20"
  -  qlx_afk_put_to_spec "1"

# **anti-rape**
- This plugin tries to detect overpowered players (for CA servers that like to maintain a certain range of skill), based on their score/second values. This plugin only works for round-based game modes. If players' score/second values are above a certain threshold (in regards to the server score/second average), an appropriate handicap will be assigned to them. This has proven to be an effective method of preventing one-sided games, ending in 0-10. The complete process of thoughts can be found in the 'handicap-thread' on the Bus Station forum. 
- CVARS
  - At the moment the values are all hard coded in the plugin itself
- COMMANDS
  - !hc [\<name\>] - Get your own or somebody elses handicap % (this can sometimes be unreadable by profile pictures)
  - !handicaps - View all the currently given handicaps and their %'s
  - !gaps [silent] - View all the players who are playing above the server average and how % they are above it. (add 'silent' if you don't want anyone to see it)
- NOTES
  - **Disclaimer:** The term 'rape' in this context is only used to describe an overpowered online player making the game unfair for others below his skill level. It is not meant in any way to offend or refer to the horrible crime that is also known under this name.

# **auto_voice_switch**
- This plugin is evaluated to be useless, since "g_allTalk 0" will automatically limit voice communication to team-only during a match. Plugin has been removed.

# **autospec**
- Displays a message during round countdown if teams are uneven, and forces the person (of the largest team) with the lowest score to spectate. If there is a big difference between teams, players will be autom. moved over.
- CVARS
  - qlx_autospec_minplayers "2" (The minimum amount of players needed on the server to work)
  - qlx_autospec_maxplayers "99" (If there are more players than this cvar, autospec won't operate)

# **centerprint**
- Provides a way to broadcast a message on everyone's screen, or just to individual people. Handy for important server announcements. Also shows a 'One enemy left' message on the screen if people want it. 
- CVARS
  - qlx_cp_message "One enemy left. Start the hunt"
- COMMANDS:
  - !showlast - toggle on/off if you want to see '1 enemy left' message 
  - !print \<message\> - print a message to a person's screen
  - !broadcast \<message\> - print a message on everybody's screen
- NOTES
  - The showlast message only works for round-based game modes, ofc

# **disable_votes**
- This plugin will disable the ability to callvote certain things during a match
- CVARS
  - set qlx_disabled_votes_midgame "map"
  - set qlx_disabled_specvotes_midgame "teamsize, kick, clientkick"
  - set qlx_disabled_votes_permission "1"
- COMMANDS
  - !disabled - shows which votes will be disabled
- NOTES
  - For spectators, the combination of the two lists will be their restriction (unless they have permission, of course)

# **gauntonly**
- This plugin will activate a special mode when one player in a team-based gametype is left last standing against a large number of opponents. The minimum amount of opponnents needed can be specified via MAX and the special mode will turn itself off when a minimum is reached. With the default variables, a 1v5 will activate it, and if it becomes 1v2 the mode will turn off
- CVARS
  - set qlx_gaunt_min "2"
  - set qlx_gaunt_max "4"

# **funlimit**
- Annoyed with the 'fun' sounds constantly being spammed? This plugin will disable all the sounds of fun.py when a match is in progress. In between rounds it is also shortly turned on, for round-based game-types.
- CVARS
  - qlx_funlimit_messages "1" (this will display a message in chat everytime the sounds are enabled/disabled)
-  COMMANDS
  - !funsounds - This command will tell you if fun sounds are currently enabled or disabled
-  NOTES

# **intermission**
- A music plugin similar to roasticle's intermission. This plugin will loop over a specified collection of sounds/music, by playing one sound at the end of a match. Upload sounds/music in a PK3 file to the workshop for it to work.
- CVARS
- COMMANDS
- NOTES
  - Read the installation and usage in the plugin code itself

# **mybalance**
- This plugin is designed to be used TOGETHER with Mino's balance plugin, but adds some more features, like skill rating-limits for connecting players, using the elo commands by names, and applying an action to the last person on uneven teams (slay, spec or ignore).
Furthermore this plugin uses a text file in which exceptions can be placed for the elo restrictions, and adds a little bump to the elo restriction for regular players. Players falling outside the provided skill rating interval can be blocked on their connection screen, be kicked after a while on the server, or can be allowed to just spectate. Furthermore warmup reminders can be scheduled to repeat at certain intervals to remind players to ready up (if warmup takes too long). In CTF and TDM matches (no rounds), a player will be frozen in place until the teams are even again. Otherwise he is sent back to spectator. 
- CVARS
  - qlx_elo_limit_min "0"
  - qlx_elo_limit_max "1600" (set to 9999 or something to have no real upper limit)
  - qlx_elo_games_needed "10" (games needed before skill restriction is aplied) 
  - qlx_mybalance_perm_allowed "2" (players with this perm-level will always be allowed)
  - qlx_mybalance_autoshuffle "0" (set "1" if you want an automatic shuffle before every match)
  - qlx_mybalance_exclude "0" (set "1" if you want to kick players who don't have enough info/games)
  - qlx_elo_kick "1" (set "1" to kick spectators after they joined)
  - qlx_elo_block_connecters "0" (set "1" to block players from connecting)
  - qlx_elo_close_enough "20" (if block_connecters is on, you can allow some people to join the server, who are 'close enough' to the limit, and they will get a normal kick. (which can be canceled via !nokick). Example, limit is 1800, then someone with 1805 will not be blocked, but get a normal kick)
  - qlx_mybalance_warmup_seconds "300" (how many seconds of warmup before readyup messages come. Set to -1 to disable)
  - qlx_mybalance_warmup_interval "60" (interval in seconds for readyup messages)
  - qlx_mybalance_uneven_time "10" (for CTF and TDM, specify how many seconds to wait before balancing uneven teams)
  - qlx_mybalance_elo_bump_regs "[[50,100],[100,300]]" (with this cvar you can setup an elo bump for regular players (example 50 games played on server = 100 more elo allowed))
- COMMANDS
  - !limit, !limits, !elolimit - view the skill rating limits, and the action which will be performed on outliers
  - !elomin [n] - without number; shows minimum allowed glicko. with number; temporary changes the minimum glicko
  - !elomax [n] - without number; shows maximum allowed glicko. with number; temporary changes the maximum glicko
  - !rankings [A|B] - without A or B; shows which rankings are being fetched (A (normal) or B (fun settings))
  - !reminders [ON|OFF] - can turn warmup reminder messages on or off
  - !elo, !getelo - can get your own skill rating or that of someone else
  - !belo - this is like elo, but will show both your A-ranking and your B-ranking
  - !elokicked - view list of kicked people
  - !remkicked \<list-id\> - after !elokicked, you can use the ID from that list to remove them from the kicklist)
  - !add_exception \<id|name\> - adds an exception to the exception list
  - !nokick [\<name\>], !dontkick [\<name\>] - prevent a person from being kicked. (if only one player is being kicked, you dont have to pass their name)
  - !reload_exceptions - This will reload all the exceptions from the exceptions file. You will be able to see the ID's and names in the console.
- NOTES
  - If you enable strict mode (qlx_mybalance_exclude "1") and qlstats goes down, players will not be able to join the server, since they won't have enough information to prove that they fall in the right skill rating limitation.

# **myban**
- This plugin enhances all the commands of the ban plugin. With this plugin you can also pass (part of) names of players to commands, instead of ID's only.
- CVARS
- COMMANDS
  - ... all the same as the ban plugin ...
- NOTES
  - You don't have to remove the ban plugin, the loading of myban will unload it automatically

# **myessentials**
- This plugin enhances all the commands of the essentials plugin. With this plugin you can also give names, or part of names of players to call the commands, instead of ID's only.
- CVARS
- COMMANDS
  - ... all the same as the essentials plugin ...
- NOTES
  - You don't have to remove the essentials plugin, the loading of myessentials will unload it automatically
  
# **myirc**
- This plugin is an extension of Mino's original plugin, aimed to enhance it a little. It uses more colors/formatting to make messages clearer. MyIrc plugin can also connect and broadcast to/from passworded irc channels via a new cvar, and a live broadcast is shown in the topic.
- (EXTRA) CVARS
  - qlx_ircRelayChannelPw = ""
- (EXTRA) IRC COMMANDS
  - .topic - Grabs the latest server update and sets it as the topic
- (EXTRA) OIDENTD
  - Support for ident-server oidentd. Each qlds running myirc.py can have its unique ident. Quakenet requires to apply for a trust if people want more than 5 clients from the same ip, a working ident server is among their conditions. See [`here`](https://www.quakenet.org/help/trusts/connection-limit). Example for oidentd base config [`/etc/oidentd.conf`](https://gist.github.com/mattiZed/78d4d0d21c035c73efdff4f1af2040f6)  
- NOTES
  - If the plugin is not changing the topic in the IRC channel, make sure it has the required privileges (+t)
  - Preview: http://i.imgur.com/JyFsgjD.png
  
# **player_info**
- Displays some more info about a player if the info command is used, and also provides a method to check a player's scoreboard information (in big CA matches people sometimes fall off / just below the scoreboard)
- CVARS
  - qlx_pinfo_display_auto "0" (set this to 1 if you want to see automatic info upon player connect)
  - qlx_pinfo_show_deactivated "1" (while this is "1" it will display a warning when a player connects with deactivated qlstats acccount (due to cheating or other bad things))
  - qlx_pinfo_ban_deactivated "0" (set this to "1" to automatically ban players with the deactivated qlstats status)
- COMMANDS
  - !info [\<player\>] - display some information, like games played, quit frequency, glicko
  - !scoreboard - display scoreboard information when players fall 'below' it
  - !allelo [\<player\>] - for one person, display the known skill ratings of each game-mode
- NOTES

# **railable**
- This plugin can give you a message (centerprinted) when your health drops to a level where you can be killed with 1 rail. Developed for Clan Arena.
- CVARS
- COMMANDS
  - !railable (this command toggles the service on and off)
  - !railmsg \<sentence\> (with this command you can choose the msg to be printed)
- NOTES
  - This plugin will do several checks each second, so if you notice too much CPU usage, it is advised to unload the plugin
  - This plugin is not considered cheating, since you could also get your HUD to display this information

# **translate**
- Provides methods to translate any words or sentences into another language, using the Yandex Translate API. Also able to look up normal english definitions and Urban Dictionaries definitions.
- CVARS
  - qlx_translate_api_key "" 
- COMMANDS
  - !translate-last \<language-name-or-tag\> \<player\> - Translates the last 3 things the given player said into the language specified
  - !translate \<language-name-or-tag\> \<word-or-sentence\>
  - !translate en Deze zin is vertaald geweest. -> Translation: This sentence has been translated.
  - !translate Russian Understood -> Translation (en-ru): Понимал
  - !define match -> Definition: a contest in which people or teams compete against each other in a particular sport.
  - !urban bye -> UrbanDef: a nicer way to say "your f-ing ugly. get out of my face"
  - !languages - Displays all the supported languages and their tags
  - !translations - Displays all the supported translation directions
- NOTES
  - Get your FREE yandex API key here: https://tech.yandex.com/keys/get/?service=trnsl
  - Example usage: http://i.imgur.com/WL5zNOR.png


# **Donate**
When minqlbot became popular and I found out we could write our own plugins, I saw an opportunity and a vision to put my coding skills to good use and try to improve the Quake Live gameplay experience. This hobby, as I would call it, somewhat pays for its own in the satisfaction I feel of having contributed something useful to my favorite game. As I see my plugins used and liked by so many players and servers, I find all the hours spent coding well worthwhile. Since some people asked, I will provide a donation link below for any of you generous people to use. Any donations given will be incredibly appreciated and will be going straight towards the necessary stuff that keeps my motivation and creativity at their peak. (Like coffee ^^)

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.me/dsverdlo)
