# Identify AWS Console Userscript

Userscript for the AWS Console to identify the current AWS account more easily.

The script shows the _name of the current account_ in the "search" input field in the menu bar.
It also changes the _color of the menu bar_ based on rules in the script. The default rules 
color the menu bar green or red when the account name contains "dev" or "prod", respectively.

## Screenshots

!["Green menu bar for development account"](/images/screenshot-development.png)

!["Red menu bar for production account"](/images/screenshot-production.png)

## Installation

1. Install the browser plugin [Tampermonkey](https://www.tampermonkey.net/)
2. [Open the script](https://github.com/mdenburger/userscript-identify-aws-console/raw/main/identify-aws-console.user.js)
3. Click "Install"

## Customization

The rules in the `ACCOUNT_NAME_COLOR_RULES` array map AWS account names to menu bar colors. 
The first matching regular expression wins.

The `ACCOUNT_OVERRIDES` object contains AWS account IDs with specific names and menu bar colors. 
Use these overrides for exceptions to the rules in `ACCOUNT_NAME_COLOR_RULES`.

## How it works

The script extracts the current account name from the JWT token in the cookie `aws-userInfo-signed`.
The menu bar colors are based on regular expressions that match the extracted account name, 
with the possibility to add exceptions based on AWS account ID.
