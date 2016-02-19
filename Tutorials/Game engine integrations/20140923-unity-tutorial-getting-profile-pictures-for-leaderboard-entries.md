# Unity Tutorial - Leaderboards - Part 6: Getting profile pictures for Leaderboard Entries

Tutorial - Leaderboards for Unity 3D

  * [1. Introduction](/uncategorized/unity-tutorial-introduction)
  * [2. Configuring GameSparks for Facebook Authentication](/uncategorized/unity-tutorial-configuring-gamesparks-for-facebook-authentication)
  * [3. Logging in to GameSparks with Facebook](/uncategorized/unity-tutorial-logging-in-to-gamesparks-with-facebook)
  * [4. Creating And Testing GameSparks Leaderboards](/uncategorized/unity-tutorial-creating-and-testing-gamesparks-leaderboards)
  * [5. Creating Leaderboard Prefabs & Posting Scores](/uncategorized/unity-tutorial-creating-leaderboard-prefabs-posting-scores)
  * [6. Getting profile pictures for Leaderboard Entries](/uncategorized/unity-tutorial-getting-profile-pictures-for-leaderboard-entries)

This is part  6 of a 6 part tutorial, it's recommended that you look at the previous section before continuing. In this section we are going to modify the Leaderboard so it pulls in the Facebook profile picture of anyone who posts a score while logged into Facebook.

* * *

### Adding a Profile Picture Field to the Leaderboard Entry Template

We already have our basic Leaderboard functionality in place, all we have to do in this exercise is edit out work to add the ability to pull images from Facebook. Start by edting the Leaderboard Entry Prefab. Set up the scene so we can see the edits we are making on the LEaderboard by dropping the Main Menu Alpha to 0 and bringing the Leaderboard Alpha back up to 1 (Remember to reset this after making your edits) **1) Editing Leaderboard Entry Prefab** Drag the Leaderboard Entry prefab from the Prefabs folder into the Hierarchy under “Grid” (So that Leaderboard Entry is a child of Grid). We need to rearrange the template that the Leaderboard Entries are added to so that it can accommodate a Facebook Profile picture

  * Set font size to 15 on all labels
  * Drag the UserName Label over to the right
Now we should have enough space to fit the Facebook profile picture on the Panel ![](https://lh5.googleusercontent.com/YX_Syd4zMd8K1Kc3QCRqSPyMbW_OmtAovcBXfD2fFY-lwZahr5Hvuj-hdOMxFEKjqMWfGqeonOBfgZFyWrgyxHvRrHN5wfnsge-WLiWhQKlPonYGJrcMMoiX_Ny1xHwtNw) **2) Adding a Profile Picture Entry to the Prefab** We need to add a new element to the Leaderboard Entry Prefab that will hold the picture we pull from Facebook and display it on the Leaderboard. As a child of the Leaderboard Entry Prefab add a new texture via NGUI>Create>Texture. Configure the new texture as follows:

  * Rename it to “User Picture”
  * Assign texture for reference purposes, use FancyIcon
  * resize to 25 x 25
  * Drag into position on Leaderboard Entry Panel between rank and userName (in the space we just created
  * Hit “Apply” to save the prefab.
That’s our Leaderboard Entry prefab set up to take a Facebook profile picture now. Your scene should look something like this: ![](https://lh6.googleusercontent.com/b2kHZjBeScU1t6sPYezIrUGlzmJnJYAJ1ol2e21tpqoToSps3Vp4xeA_T1UarG7WsBMCjPNNeJBHkCUMaHYcMBHMQzVXmqZQnvsTOIOkw9-gzze3lcLwNLmhQRY68n6AzA) Now we just need to edit some of our Leaderboard scripts so that they will pull and apply the Facebook profile pictures to the Leaderboard.

* * *

### Editing Leaderboard Scripts to pull Profile Pictures

  **Edit Code** The two scripts we have to edit are the “Leaderboard Entry” script and the “Leaderboards” script. ** 1) Update Leaderboard Entry Script** We need to add a function to our Leaderboard Entry script that will add take the profile picture and add it to the Leaderboard Entry. The code is below, it’s a modified version of the Leaderboard Entry script we wrote last exercise with comments on the additions made,


    using UnityEngine;
    using System.Collections;

    public class LeaderboardEntry : MonoBehaviour {

            //add a new string to refernce when adding the picture to the
            //leaderboard entry
            public string rankString, usernameString, scoreString, facebookID = "";

            public UILabel rank, username, score;

            //Create this variable so we
            //can define what textue we are updating
            public UITexture profilePic;

            // Use this for initialization
            void Start()
            {
                    rank.text = rankString;
                    username.text = usernameString;
                    score.text = scoreString;
           // Defines when the image will be pulled
                    if (facebookID != "")
                    {
                            StartCoroutine(getFBPicture());
                    }
            }

            //this is the function that will pull the profile picture from
            //facebook public IEnumerator getFBPicture()
            {
                    var www = new WWW("http://graph.facebook.com/" + facebookID + "/picture?type=square");

                    yield return www;

                    //make sure the dimensions of the new texture match what we set                 //up in the Leaderboard Entry prefab
                    Texture2D tempPic = new Texture2D(25, 25);

                    www.LoadImageIntoTexture(tempPic);
                    profilePic.mainTexture = tempPic;

            }

    }

  **2) Update Leaderboards Script**

We need to update the Leaderboards script to pull in the Facebook ID’s from the Leaderboard information stored on the GameSparks servers. It’s just line but we’ve added the whole script below just in case.


    using UnityEngine;
    using System.Collections;
    using System.Collections.Generic;
    using GameSparks.Api.Requests;


    public class Leaderboards : MonoBehaviour
    {

            public GameObject leaderboardEntryPrefab;

            public UIGrid leaderboardGrid;

            public List<GameObject> entries = new List<GameObject>();

            void Start()
            {
                    leaderboardGrid.Reposition();
            }

            public void GetLeaderboard()
            {

                    for (int i = 0; i < entries.Count; i++)
                    {
                            Destroy(entries[i]);
                    }

                    entries.Clear();

                    new LeaderboardDataRequest_highScoreLeaderboard().SetEntryCount(10).Send((response) => {

                            foreach (var entry in response.Data)
                            {

                                    GameObject go = NGUITools.AddChild(leaderboardGrid.gameObject, leaderboardEntryPrefab);

                                    go.GetComponent<LeaderboardEntry>().rankString = entry.Rank.ToString();
                                    go.GetComponent<LeaderboardEntry>().usernameString = entry.UserName.ToString();
                                    go.GetComponent<LeaderboardEntry>().scoreString = entry.GetNumberValue("score").ToString();
                                    //this is the line we add to pull the facebookID from GameSparks.
