# Snapshots

[toc]

Snapshots feature allows you to *Create*, *Copy*, *Delete*, *Publish*, *Revert* and *Preview* the configuration of your Game, allowing for in-depth management of each stage of the release.

# Creation & Basics of Snapshots

You can create a Snapshot of the current game configuration by pressing the '+' button in the Snapshots section on the Overview page.

![](img\Snapshot\1.png)

This will display a form where you'll have to enter some meaningful description of the snapshot.

![](img\Snapshot\2.png)

Clicking Save will then create the Snapshot. Where you will then be able to access additional options.

![](img\Snapshot\3.jpg)

  * *Copy* \- copies the snapshot to create a new or overwrite an existing game. You can overwrite only a game that you are an owner or admin of. You will have the option to either copy just the metadata from the original Snapshot, just the game configuration, or both. Don't worry about overwriting the target games configuration. There is a fail-safe - a snapshot of the target games previous version is automatically created (called "AUTOSAVE - Pre Copy") before the copy occurs.
  * *Delete* \- will delete the snapshot.
  * *Publish* \- publish the configuration to the LIVE servers. The snapshot that is currently published is highlighted in green. See below for more detail on publishing.
  * *Revert* \- updates your workspace with the selected snapshot version. There is another fail-safe - a snapshot of the previous version is automatically taken (called "AUTOSAVE - Pre Revert").
  * *Preview* \- allows previewing any of the Snapshots without having to revert to them, editing will be disabled when previewing.

# Copying a Snapshot

When copying a Snapshot you will be presented with a form that allows a number of selections to be made, each allowing you to customise what you want to be copied over. You will have the option to either copy just the metadata from the original Snapshot, just the game configuration, or both.

![](img\Snapshot\4.jpg)

  * *Game* \- from the drop-down, you can choose to copy the Snapshot to a new game or to overwrite an existing game that you have access and permissions to edit.
  * *metadata* \- choose whether to include the metadata for the copy of the game.
  * *configuration* \- choose whether to copy the game configuration onto an existing game, overwriting any existing configuration. When copying to a new game, this option is disabled as it will always copy the Snapshot's game configuration.

# Deleting a Snapshot

By pressing delete you will be prompted with a confirmation form. Press *Delete* to confirm only when you are absolutely sure.

![](img\Snapshot\5.jpg)

# Publishing a Snapshot

Publishing a Snapshot places the configuration of the game into the LIVE environment, where the game can then be accessed by your players. For in-depth tutorial on versioning read [here](../Versioning and the Publishing Process\Versioning and Publishing.htmhl).

![](img\Snapshot\6.jpg)

Once you confirm your selection to publish the Snapshot, it will be highlighted in green within the list of Snapshots as seen below:

![](img\Snapshot\7.jpg)

# Reverting a Snapshot

It may be that you want to revert to earlier version of your game configuration or saved metadata collections if you accidentally removed some config or something recently went wrong. When Reverting a Snapshot you will be prompted for a confirmation.

![](img\Snapshot\8.png)

Additionally when reverting a Snapshot you will notice that we save your current configuration and create an automatic Snapshot of everything as it was before the revert.

![](img\Snapshot\9.jpg)

# Previewing a Snapshot

Previewing a Snapshot allows you to view the game configuration of that Snapshot without having to reverting to it then revert back to your original state. In Snapshot Preview mode, all editing is disabled during the preview and you will see an indication of what's being previewed at the top of GameSparks Configurator.

![](img\Snapshot\10.jpg)

The Snapshot Preview header is an informative notification of what Snapshot you are currently previewing, when it was created, whether it is live or not and who it was created by. By clicking the 'Exit Preview' button or navigating away from the Configurator, you will exit the preview.
