# Open Source Intelligence \(OSINT\)

`TARGET` is used to represent the username of the person/ account that you're actually targeting.

## Tools

### Facebook

* [Stalkscan](https://stalkscan.com/) - “All 'public' info Facebook doesn't let you see”

### Twitter

* [Twitter Advanced Search](https://twitter.com/search-advanced)
* [Social Bearing](https://socialbearing.com/)
* [Sleeping Time](http://sleepingtime.org/) \(Requires sign in\)
* [tweet-device.py](https://github.com/0xmachos/python-scripts/blob/master/tweet-device.py) See devices used to tweet \(Requires API keys\)

## Techniques

### Twitter

#### Birthday

Find Tweets that mention `TARGET` and contain the words `Happy`, `Birthday`, or `bday`.

```text
https://twitter.com/search?l=&q=Happy%20OR%20Birthday%20OR%20bday%20%40TARGET
```

#### Family

Scroll to bottom of:

* `https://twitter.com/TARGET/following`
* `https://twitter.com/TARGET/followers`

`CTRL` + `F`, search for `TARGET`'s last name.

You probably want to [script](http://www.tweepy.org/) this for accounts with a large number of [followers](http://docs.tweepy.org/en/v3.5.0/api.html#API.followers_ids)/ [following](http://docs.tweepy.org/en/v3.5.0/api.html#API.friends_ids).

### Facebook

#### Family

```text
https://www.facebook.com/TARGET/friends
```

If `TARGET`'s friends list is public, search for `TARGET`'s last name via search box.
