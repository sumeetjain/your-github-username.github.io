# Student Journal

You'll use this to publish your journal. Follow the below steps carefully, and there shouldn't be any issues.

## Start Here

1. Fork this repository. Don't clone it yet!
2. From _your_ copy, go to Settings. ([Demo](http://cl.ly/f5fG/Screen%20Recording%202016-02-08%20at%2002.03%20PM.gif))
3. There, you should rename this repository to user **your actual GitHub username**. So in my case, I would rename the repository to `sumeetjain.github.io`. ([Demo](http://cl.ly/f5as/Screen%20Recording%202016-02-08%20at%2002.05%20PM.gif))
4. Then go back to the repo's main page and clone the repo into your **~/Code** folder as you usually would for other assignments.

### Once it's cloned...

Now you have a folder like **~/Code/sumeetjain.github.io** (except with your GitHub username--not mine).

`cd` into that. Then run `jekyll server`.

Just like with Sinatra, this starts a web server. So you shouldn't expect to get the command-line prompt back until you `Control + C` to quit the server.

The name of this web framework is [Jekyll](https://jekyllrb.com/). In a sentence, it takes the Markdown files you give it and converts them into a website.

If you still have the server running, go to <http://localhost:4000>. It's a website! It's _your_ website!

### Making it truly yours...

#### 1. Site Title

Open the **_config.yml** file and change the name to yours. This can be anything you want actually--your real name, favorite screenname, etc. It's the title of your website.

I suggest just using your name, since it can be hard to predict what little, silly thing might make an employer or some other valuable contact close your website.

#### 2. Your Content

Now it's time to add your journal entries!

Let's first copy over the journal entries from your Journal. I suggest making new files using Sublime and then copying over the text from each journal entry.

![](http://cl.ly/f5OW/Screen%20Recording%202016-02-08%20at%2002.30%20PM.gif)

Name them very precisely: `yyyy-mm-dd-title-of-entry.md`. See the example entry's filename if you're still unsure.

(Your existing journal entries probably have a name format like `mm-dd-title-of-entry.md`--missing the year, that is. Make sure to add the year to filenames for this. They're important.)

Once you've copied over your entries, you'll need to make one small addition to them all:

```
---
title: The Title of The Entry Like This
---

```

Add this to the _very_ top of each entry. (And change the title to the actual title.)

Again, you can refer to the example entry to see how it's done. When you're done, delete the example entry.

#### 3. About Page

Add a little content to start with in **about.md**.

## Try it out!

Save everything, run `jekyll server`, and then go to <http://localhost:4000>. You should see your posts.

If things aren't working out, open a PR with all of your code pushed up and let us help out.

### Publishing

If it works locally, you're ready to push to GitHub.

```
git add .
git commit -m "First commit"
git push
```

(If `git push` alone doesn't work, try `git push -u origin master`.)

Then go get a cup of coffee or something, and when you come back try to go to <http://your-github-username.github.io> (except with your real username).

It should work! That website is live!