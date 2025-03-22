## Uninstalling Fate

Ares plugins plug IN easily, but taking them out requires a bit of code fiddling.

1. Open the [tinker](https://aresmush.com/tutorials/code/tinker.html#how-to-tinker) page (Admin -> Tinker) in the web portal with a coder character.

2. Copy/paste the following to the tinker file, **right below `module AresMUSH`**. This will let us clear out the database fields.
 
```
   class Character
      attribute :fate_aspects
      attribute :fate_stunts
      attribute :fate_skills
      attribute :fate_points
      attribute :fate_refresh
    end
```

3. Add the following code to the `handle` method of the tinker file, right after `def handle`.
 
```
    Fate.uninstall_plugin(client)
```

4. Click "Save" on the tinker page.

5. Switch to a game client window and run the `tinker` command with a coder char.

6. Switch back to the web portal tinker page and click "Reset".

7. Manually remove all plugin's files from your server (and GitHub fork, if applicable), including:
    * aresmush/plugins/fate
    * aresmush/game/config/fate_*.yml
    * Web portal files - See the /webportal folder in this repo for a specific list of files.

8. [Restart the game engine](https://aresmush.com/tutorials/manage/shutdown.html).