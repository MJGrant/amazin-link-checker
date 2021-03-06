# Amazin' Affiliate Link Checker

![alt text](screenshots/amazon-may-26-2019.png "Amazin' Link Checker screenshot 5/26/2019")

This github repo contains the tool's codebase and is made public as an example of my work. You can use the tool without cloning this repo by visiting it at (URL coming soon). 

## Who this tool is for
This tool is intended for Amazon Associates ("affiliates") with established websites.

## Why use this tool
For a variety of reasons, your site's Amazon.com product links may become outdated. When this happens, your visitors end up on 404 pages ("dog pages") instead of the product(s) you meant to show them. This tool helps you quickly locate those dead links.

## How it works
This tool scans your article for Amazon product links. It extracts a product ID from each link and checks that the product ID is valid. This website does not store your credentials or anything about your site.

## Interpreting your results
Unfortunately, not every product on Amazon is in the Amazon Product Advertising API. Valid links may be marked "invalid" by this tool if the product doesn't exist in the API. The tool also considers links to Amazon.com search results to be "invalid" even though they are perfectly acceptable to Amazon and your site's users. You should manually confirm any "invalid" results you get.

## To run locally:

1. Clone both this repo (the client) and the [server repo](https://github.com/manderly/amazin-link-checker-server)
2. Open a terminal window for each repo
3. In server, ```npm install``` and ```node app.js```
4. In client, ```cd amazin-app```, then ```yarn install```, and finally ```yarn start``` 
5. In your browser go to ```localhost:3001```

### Running tests

#### Integration tests

From the **server** repo: 

```nightwatch frontend.js``` runs integration tests. Requires client running (in another tab, navigate to client repo and use ```npm start```)

#### Unit ("react snapshot") tests

From the **client** repo:

```yarn test``` rebuilds snapshots and runs unit tests

```yarn test-u``` runs unit tests on existing snapshots

## Deploying

1. In the ```client``` repo, use ```yarn run build``` to create a folder called ```build```
2. Copy the **contents** of ``build`` (ie: not the build folder but what's inside it)
3. Go into the ```server``` repo directory
4. Open the ```public``` folder
5. Delete all of the files inside public
6. Paste the contents of build into public
7. Push this change to GitHub
8. Use ```git push heroku-amazin master``` to push these changes to Heroku
9. Use ```heroku open``` to open the app

Troubleshooting:
If the heroku repo isn't hooked up (403 when trying to push to heroku), follow these steps:
1. In Terminal, ```heroku login``` and follow the steps to log in
2. Still in Terminal, enter ```heroku git:remote -a amazin-link-checker```
3. For clarity and to avoid confusion with other Heroku remotes, I renamed this one to heroku-amazin ```git remote rename heroku heroku-amazin```
4. Now the push can be done with ```git push heroku-amazin master```


## Want to make it better?
Make a pull request and I'll check it out!

## About me

I'm a Chicago-based web developer who thought it might be fun to automate the tedious process of hunting outdated Amazon links on my blog.
