# How to deploy apps to Heroku


### Prerequisites
* We will assume you already have a discord developer account from which you can get your tokens, etc. Start [here](https://discordapp.com/developers/applications/) if not.
* If you are reading this on GitHub, we will also assume you already have an account. Otherwise, if you are reading this on [Hashnode](https://hashnode.com/@mikeysan/joinme), sign up for a [GitHub](https://github.com/join) account.
* Finally, we make no assumptions here. You will need to sign up for a Heroku account. You can do that [here](https://signup.heroku.com/).


## Let us begin:

### Create
* Once you have setup your account on heroku, visit [apps-dashboard](https://dashboard.heroku.com/apps) to setup the app.

* Click "New" and select "create cew app".

<img align="left" src="https://github.com/mikeysan/articles-and-thoughts/raw/main/images/create_new_app.PNG">
<br clear="left" />

* Give the app a name and select a region.

<img width="70%" height="70%" align="left" src="https://github.com/mikeysan/articles-and-thoughts/raw/main/images/give-name-n-region.PNG">
<br clear="left" />

* Next click on "Create app".

### Deploy
* Next you will be taken to the "Deploy" tab when you decide how you want to deploy your app. We will select "GitHub".
<img width="70%" height="70%" align="left" src="https://github.com/mikeysan/articles-and-thoughts/raw/main/images/deploy_selection.PNG">
<br clear="left" />

###### Note: For each deployment method you choose, Heroku will display steps on how to proceed. For example, deploy using Heroku CLI

<img width="70%" height="70%" align="left" src="https://github.com/mikeysan/articles-and-thoughts/raw/main/images/deploy-w-herokucli.PNG">
<br clear="left" />

* Follow instructions on Heroku to connect your GitHub account to heroku.

* Once you have connected your GitHub account to Heroku, you should see it under "Search for a repository to connect to.
<img width="70%" height="70%" align="left" src="https://github.com/mikeysan/articles-and-thoughts/raw/main/images/deploy-w-github.PNG">
<br clear="left" />

* Search for a repository you wish to connect to (deploy). My example shows which repositories come up as I search for twitter.

<img width="70%" height="70%" align="left" src="https://github.com/mikeysan/articles-and-thoughts/raw/main/images/search-for-repo.PNG">
<br clear="left" />

* Choose which branch you wish to deploy. You can choose between the "development"(if you have one) or "main".

* Once you have connected your repository with heroku and decided on which branch to deploy you will now have to pick between:
    * Automatic deploys or
    * Manual deploy

* This final step is up to you to decide. My advice is to start with Manual if you are still developing your app. Unless you already have a CI service in place (as adviced by Heroku).

### Additional Tips
* Please contribute any steps you think might be helpful to others
