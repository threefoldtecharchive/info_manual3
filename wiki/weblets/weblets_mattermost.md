# Mattermost

[Mattermost](https://mattermost.com/) A single point of collaboration. Designed specifically for digital operations.


!!!include:weblets_play_go
- Make sure you have an activated [profile](weblets_profile_manager)
- Click on the **Mattermost** tab

__Process__ :

![](img/mattermost1.png)

- Enter an Application Name. It's used in generating a unique subdomain on one of the gateways on the network alongside your twin ID. Ex. ***matter*.gent02.dev.grid.tf**

- Select a capacity package:
    - **Minimum**: {cpu: 1, memory: 1024 * 2}
    - **Standard**: {cpu: 2, memory: 1024 * 4}
    - **Recommended**: {cpu: 4, memory: 1024 * 4 }
    - Or choose a **Custom** plan

- Select a node to deploy your MatterMost instance on.

- Either use the **Capacity Filter**. Which simply lets you pick a *Farm* and *Country*, after clicking on *Apply filters and suggest nodes* then it lists available nodes with these preferences and you pick.


- Or use **Manual** and type a specific node number to deploy on.

- Mattermost requires an SMTP server. So make sure you have one configured and fill the fields with its credentials.

After that is done you can see a list of all of your deployed instances

![](img/mattermost4.png)

Click on ***Visit*** to go to the homepage of your Mattermost instance! You need to login using TFConnect so make sure you download the *TFConnect* app from your App Store.

![](img/mattermost5.png)
