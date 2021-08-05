# Discord

## 09/05/2021

* Added a grads channel

## 01/05/2021

* Added previous committee channel and transferred last year's committee into the previous committee role
* Revamped the permissions system entirely
  * Added a Verified role and moved the permissions system to it rather than Member and Grad \(now vanity\) roles
  * Revoked implicit permissions from every role other than @everyone and Committee for easy permission handling
  * Reset explicit channel permissions and moved to implicit category permissions for roles where possible \(setting overrides where necessary\)
    * @everyone has read access to some of the Important category
    * Student Association has the same access, with a couple more Important Channels
    * Verified has access to virtually everything other than the Committee channels. No write access to important channels
    * Abertay Staff have similar access to Verified, but with no access to the help channels
* Added the Bot role and assigned it to the hacksoc bot
* Moved Sarah's welcome messages to the bot
* Revamped the category design to include emojis
* Removed the Fresher role from previous year freshers
