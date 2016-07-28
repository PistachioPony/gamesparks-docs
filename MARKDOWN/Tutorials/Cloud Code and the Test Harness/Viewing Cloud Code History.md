---
nav_sort: 2
src: /Tutorials/Cloud Code and the Test Harness/Viewing Cloud Code History.md
---

# How to view Cloud Code History

You can manage your Cloud Code revisions between Snapshots. This allows you to review and revert to previous versions of the Cloud Code that appears on Events and provides a visual comparison showing the differences in the Cloud Code.

## Accessing Cloud Code History

*1.* To access Cloud Code History, navigate to the *Cloud Code* section in the *Configurator* and select the *History* button:

![](img/CloudHistory/1.png)

This opens the Cloud Code History tool:

![](img/CloudHistory/2.png)

The Cloud Code History tool is designed to allow you to select one Snapshot - from the *Base* column - then select a second Snapshot - from the *Compare to* column - and then compare the Cloud Code contained in the two Snapshots.

## Comparing Snapshots

The Cloud Code History tool is designed to be read right-to-left:
* The left column - *Base* - shows the current Workspace Configuration and latest saved Snapshot of the game.
* The right column - *Compare to* - shows all other snapshots that pre-date the one that is selected in the *Base*.

**Left Column**  | **Right Column**
-----  | -----------
  ![](img/CloudHistory/3.png)  | ![](img/CloudHistory/4.png)
   Selecting Snapshot *8* in *Base*... | ...shows all Snapshots older than Snapshot *8* in *Compare to*

</br>
<q>**Green is LIVE!** Any Snapshot highlighted in green is the one published to LIVE.</q>

## Identifying Differences

### Using the Differences Drop-Down

In the far-right of the screen, there is a drop-down labelled *Differences.* Depending on the comparison of Snapshots, it will show the items (and their location) that differ between those Snapshots. For example, new events added, edited events, and ones that have been removed:

*Key:*

![](img/CloudHistory/5.png) - Newly added item since *Compare to* Snapshot version

![](img/CloudHistory/6.png) - Edited item since *Compare to* Snapshot version

![](img/CloudHistory/7.png) - Removed item since *Compare to* Snapshot version

![](img/CloudHistory/8.png)

### Checking Lines of Cloud Code

Lines of Cloud Code highlighted in blue depict the difference for that module or event where the Cloud Code differs:

![](img/CloudHistory/9.png)

### Cloud Code Equivalent Snapshots

The *Base* column will only show Snapshots with Cloud Code differences from each other. It won't show Snapshots that are the same as each other.

**Left Column**  | **Right Column**
-----  | -----------
  ![](img/CloudHistory/10.png)  | ![](img/CloudHistory/11.png)
   Selecting Workspace Configuration in *Base*... | ...shows all Snapshots older than Snapshot *11* in *Compare to*

However, if Snapshots *5* and *6* are Cloud Code equivalent and we then select Snapshot *6* in Base:

**Left Column**  | **Right Column**
-----  | -----------
  ![](img/CloudHistory/12.png)  | ![](img/CloudHistory/13.png)
   Selecting Snapshot *6* in *Base*... | ...shows Snapshot *4* and older in *Compare to*


![](img/CloudHistory/10.png) ![](img/CloudHistory/11.png)

*Base* column                                                                                                                          *Compare to* column

![](img/CloudHistory/12.png) ![](img/CloudHistory/13.png)

Setting the *Base* to Snapshot *6* will let us compare only to Snapshot *4* and earlier.

For example, in terms of the Cloud Code on my game, Snapshots *1* to *4* (including the AUTOSAVE Snapshot) are the same as each other. Actually, these Snapshots have little or no Cloud Code at all. Snapshots *6* to *11* are all different from one another. Snapshots *5* and *6* are the same as each other - I know this because if I select Snapshot *6* in the *Base* column, Snapshot *5 *is not available in the *Compare to* column.

However, we already know that Snapshot *5* is different to Snapshot *1* and separately, Snapshot *5* is different to Snapshot *2*. Therefore we can compare Snapshot *5* in the *Base* column to Snapshot *2* or Snapshot *1*, but it would be tedious to compare Snapshot *4* to Snapshot *2* or compare Snapshot *3* to Snapshot* 1 because the platform already knows the result would be the same. Are you still with me? Good, because we're trying to save you time!
