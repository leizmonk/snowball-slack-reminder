### What is this?
Snowball is a Slackbot that will periodically send reminder messages to designated users in specified GitHub organizations about:
  - pull requests that they have been asked to review
  - changes requested by reviewers on a pull request (sent to PR author)
  - approved pull requests that have not been merged (sent to PR author)

The inspiration behind this project came from an engineering team retrospective at the project author's company (<a href="http://www.phido.io/" target="_blank">Phido.io</a>) in which team members expressed that these types of reminders get lost in email. A decision was made that a Slackbot would offer a better delivery system for such reminders.

It is a revamp of <a href="https://github.com/Ahmadposten/Github-slack-reminder">an existing library</a>, but implemented with JavaScript Promises.

Its character and avatar are based off the <a href="http://rickandmorty.wikia.com/wiki/Snuffles" target="_blank">eponymous dog</a> in the animated series Rick and Morty. 

Link to GitHub: <a href="https://github.com/leizmonk/snowball-slackbot" target="_blank">snowball-slackbot</a>

### Installation
- Clone this repo (if not using npm) then `npm i`, see section on execution after the rest of these setup steps
- If using npm, `npmi -g snowball-slackbot`

### Additional Setup
- Create a config file in your local home directory named `.ghslackuser` with mappings of your org's GitHub users and their corresponding Slack usernames like:`{ "l337hackerGH": "slackerelite" }`
- Create a config file in your local home directory named `~/.ghslackids` with a mapping of your org's GitHub user names to their corresponding Slack user IDs like: `{ "l337hackerGH": "U4ZAQH555" }`
  - Here's a quick way to get your org's Slack user IDs that you want to include: https://stackoverflow.com/questions/40940327/what-is-the-simplest-way-to-find-a-slack-team-id-and-a-channel-id
- Set up a new bot in your org's Slack account
  - Go to `https://YOUR-ORG.slack.com/apps/manage/custom-integrations`
  - You will get an API token for your bot. Save this in your `.bashrc` or `.bash_profile` as `REMINDER_TOKEN`. This is required for the bot to connect to your Slack acount.
  - You can name your bot whatever you want and use this library but for the sake of some fun easter eggs, I'd recommend sticking with snowball and <a href="https://s3-us-west-2.amazonaws.com/slack-files2/bot_icons/2017-05-24/186775348656_48.png" target="_blank">using this avatar</a>.
- Set up a GitHub API token. Save this in your `.bashrc` or `.bash_profile` as `GITHUB_TOKEN`. This is required for the bot to read from your GitHub orgs and repositories.
- Save a comma separated list of GitHub orgs you want the bot to monitor as `ORGANIZATIONS` in your `.bashrc` or `.bash_profile`.

### Options
This bot will operate by default between 10AM and 6PM local time, Monday through Friday, on a 2 hour interval.
- Change work hours by modifying the values of the `workStart` and `workEnd` variables on lines 13 & 14 of `snowball.js`.
- Save a custom integer value for `GITHUB_SLACK_REMINDER_INTERVAL` in your `.bashrc` or `.bash_profile` if you don't want to use the default value of 2 (hours).

### Usage
You need Node 8+

If you've cloned this repo directly off of Github:
- From the root folder of the repo: `cd lib/ && node index.js`

If you've installed this as an npm module, just run `snowball` in your terminal


### Slack Commands
You can use the following commands with the bot running in Slack:
- `snowball-snooze` if you want to shut off reminders for the rest of the workday. Reminders will resume the next day.
- `snowball-resume` if you want to resume getting reminders.
- `snowball-fetch` to get on demand reminders. If you have no reminders pending, this command won't do anything (you won't get a message back).

Contact me if you have setup problems. Report any bugs you find. Feel free to comment on requests for additional features or contribute to this project. I'm a product manager and not full on programmer by trade so contributions, refactors, etc are more than welcome!
