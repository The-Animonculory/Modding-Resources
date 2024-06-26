# Editing cells from esl files - By Styxx

## ESM Flagged Files

ESM-flagged files are not **"not persistent"**. Persistent and temporary records from ESM-flagged files are correctly treated as either persistent or temporary and loaded/unloaded accordingly, whereas in non-ESM flagged files, all records are treated as persistent. This is the cause of the SSE reference handle limit, when too many ESPs have too many references, when only a finite number can be loaded at any given time. If an SKSE plugin (or future game update) fixed this in order to fix the reference handle limit, the bug would affect cells in ESL-flagged files as well.

## Creation Club Survival Mode

The cell from CC Survival Mode being referenced does originate in that plugin, and it does contain temporary records, but it isn't a gameplay cell; players probably won't be traveling to it while playing, nor is it particularly likely that another mod will come along and edit the same cell and send the player to it, so as far as issues go, it should be safe to consider it benign.

## Unofficial Myrwatch Patch

In the case of the Unofficial Myrwatch Patch, it works because the cell record being edited has the Partial Record (<unknown 14 flag in xEdit>) flag in the patch plugin, not because it's only editing persistent references (which it also isn't doing, it adds a few new persistent references as well, and the original plugin contains plenty of temporary references itself). 

The Partial Record flag effectively flips the bug so that instead of ignoring the original cell's temporary references, the overwriting cell's temporary references are ignored instead. Additionally, while this method does work for some mods like the Myrwatch Patch, in some cases the cell record may need to be edited, in which case flagging the override as a Partial Record wouldn't work.

## Temporary References

You also can edit temporary references from a cell originating in an ESL-flagged file, you simply need to mark the reference as persistent, and ensure the cell record is flagged as a Partial Record.

So having said that, a more correct set of conditions would be:

- The plugin is ESL-flagged, as the distinction here between ESM-flagged plugins only exists due to a separate bug.
- The plugin contains new cell records that are overridden by another plugin in the load order, and the overwriting record is not flagged as a Partial Record. Marking all references in a cell as persistent is a bad practice and will just contribute extra bloat to the reference handle limit.
- The overwriting plugin is flagged as a Partial Record but contains temporary references that will not be loaded.

In a load order with all of the CC content and Unofficial Patches, the Survival Mode plugin would not raise any red flags, because nothing would be overwriting its cell record. The Unofficial Myrwatch Patch would also not raise any red flags, because it correctly flags the overridden cell record as a Partial Record, and itself only contains persistent references (some edited from the original plugin, some new.)

## Credits:

Full credit to [shad0wshayd3](https://www.nexusmods.com/skyrimspecialedition/users/5232181) who explained that in the comment section of a random mod page.
I just copied what they said as it may help others
