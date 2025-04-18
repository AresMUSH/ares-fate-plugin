# Fate

## Status

**Supported**  Although not part of the main Ares code release, this is a supported plugin.  [Report](https://aresmush.com/feedback) any problems you encounter.

See release notes to determine which versions of AresMUSH are compatible.

> Note: This code has been run through its paces on a test server, but hasn't been playtested on a real game yet.   The first game to implement this will receive extra technical support from Faraday to iron out any bugs.


## Overview

This plugin is a simplified implementation of the Fate RPG system.  

    +==~~~~~====~~~~====~~~~====~~~~=====~~~~=====~~~~====~~~~====~~~~====~~~~~==+
    Gates        Approved        
    -----[ Aspects ]--------------------------------------------------------------
    Always A Klutz
    Gun For Hire
    
    -----[ Skills ]---------------------------------------------------------------
    Athletics:       Fair                Crafts:          Good                
    Drive:           Good                Empathy:         Good                
    Fight:           Good                Notice:          Fair                
    Resources:       Average             Shoot:           Great               
    Will:            Great               

    -----[ Stunts ]---------------------------------------------------------------
    Crane Kick - Add Two To Finishing Moves.
    Dazing Counter - See stunts list.

    Refresh: 3                              Fate Points: 1
    +==~~~~~====~~~~====~~~~====~~~~=====~~~~=====~~~~====~~~~====~~~~====~~~~~==+

    %% Opposed Roll: Faraday/Will - Superb (5) vs Kitty/Good - Good (3).  Faraday wins.

## Web Portal

This plugin includes a simple sheet display on profiles and a way to roll skills in a scene. There is no chargen support.

## Refresh

Fate points in the core mechanic are refreshed every "session".  You'll need to decide what constitutes a "session" for your game and trigger the refresh accordingly.  Some games may do a refresh monthly; others may do so after a natural break in the metaplot.  It's up to you.

### Manual Refresh

Admins can trigger a manual refresh at any time using the `fate/refresh` command.

### Automated Refresh

An automated refresh is disabled by default.  You can enable it by setting the `refresh_cron` configuration option to perform the refresh at a set interval (e.g. weekly or monthly).  See the [Cron Configuration Tutorial](https://www.aresmush.com/tutorials/code/cron/) for more information on possible settings.

## Installation

1. Disable the FS3 plugins, as explained in [Enabling and Disabling Plugins](https://aresmush.com/tutorials/config/plugins/).
2. In the game, run `plugin/install <github url>`.
3. Go to Admin->Setup and change your [chargen stages](https://aresmush.com/tutorials/config/chargen.html).  Replace the FS3 stage with stages for FFG:

Old:

    abilities:
      help: skills

New:

    fate:
      help: fate
    abilities:
      help: abilities

Additional configuration options are described below.

## Configuration

This plugin has several configuration options:

### Starting Limits

You can configure how many stunts and aspects characters are allowed to start with.

* `max_starting_aspects`
* `max_stunts`

### Starting Skills

You can configure how many skills a character can start with at different levels.  Any level not listed has no limit.  For example, the standard Fate skill pyarmid allows 4 skills at Average(1), 3 at Fair(2), 2 at Good(3) and 1 at Great(4).  No skills are allowed at ratings above Great.

    starting_skills:
        "Average" : 4
        "Fair" : 3
        "Good" : 2
        "Great" : 1
        "Superb": 0
        "Fantastic": 0
        "Legendary": 0

### Stress Skills

You can configure which skills are used to calculate physical and mental stress:

    physical_stress_skill: Physique
    mental_stress_skill: Will

### Skill List

You can configure the list of available skills, with a description for each.

    skills:
        - 
            name: Athletics
            description: "General physical fitness and feats like running, jumping, etc."

### Sample Stunts

You can configure a list of sample stunts for people to choose from, but players can also create their own stunts.

    stunts:
        - 
            name: Sprinter
            description: "Double free movement."

## Uninstalling

Removing the plugin requires some code fiddling.  See [Uninstalling Fate](Uninstalling.md).

## License

Same as	[AresMUSH](https://aresmush.com/license).
