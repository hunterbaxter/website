---
title: Using RSS
summary: aggregating all content feeds (including my site) into one place
date: 2022-01-05T00:00:00-06:00
showToc: true
tags: [tech]
ShowReadingTime: true
---

# What is RSS
[RSS = Really Simple Syndication](https://en.wikipedia.org/wiki/RSS).
RSS essentially creates a custom newsfeed of content from subscribed sites in a platform-agnostic way.
So, instead of checking every site one wants updates from, one checks a single place.
Only viewing an RSS feed reader can drastically reduce the amount of time one spends online.
One might ask, "Isn't an RSS feed just a social media feed?"
Yes, it is theoretically the same.
However, you have pure control with RSS, unlike modern social media providers.
A prototypical RSS feed recommends nothing, promotes nothing, and is unconcerned with how long one scrolls.

# RSS Feed Readers
## Desktop and Mobile Readers
For desktop and mobile, there are many RSS feed readers.
[Feedly](https://feedly.com/), [Inoreader](https://www.inoreader.com/), and [Newsblur](https://www.newsblur.com/) all seem really user friendly, but I have not tried them.
I recommend using whichever reader is most minimal.
Feedly, Inoreader, and Newsblur all have Web, iOS, and Android interfaces.

## Terminal User Interface (TUI) Readers
I personally like TUIs (terminal user interfaces), so I use [newsboat](https://newsboat.org/) for my RSS reader.
Using newsboat is very simple, and one can install it via their package manager (dnf for fedora), or from source ([instructions](https://github.com/newsboat/newsboat)).
To configure newsboat, check out the [arch linux user wiki](https://wiki.archlinux.org/title/Newsboat). Also, my configurations can be found in my [.dotfiles repository](https://github.com/baxterhc/.dotfiles/blob/master/.config/newsboat/config).
All one has to do is put my URL in their newsboat url file (mine is located at '$HOME/.config/newsboat/urls' like below:
``` sh
https://baxterhc.github.io/rss.xml
```

# Subscribe to my site
Paste my [rss feed link](https://baxterhc.github.io/rss.xml) into your desired RSS provider.
``` sh
https://baxterhc.github.io/rss.xml
```

# Bonus
## Subscribe to a Youtube Channel
Youtube does not make getting an RSS feed for a channel trivial.
However, it can be done with minimal effort if one knows where to look.
First, one needs to find the channel id for a channel.
One can find the channel id by viewing the raw html page for the channel.
Unfortunately, I do not know how to do this on mobile, but on a browser, one should be able to right-click and then select "View Page Source" (at least on Firefox) to view the raw html.
Then, search for "channelId" inside the html file.

``` html
<meta itemprop="channelId" content="some_id">
```
Then, paste the following (with some_id replaced with actual channel id) into ones RSS provider.
``` sh
https://www.youtube.com/feeds/videos.xml?channel_id=some_id
```

## Feeds I like
[CMU Software Engineering Institute](https://insights.sei.cmu.edu/blog) ```https://insights.sei.cmu.edu/blog/feeds/latest/rss```

[MIT Technology Review](https://www.technologyreview.com/) ```https://www.technologyreview.com/feed```

[IEEE Spectrum](https://spectrum.ieee.org) ```https://spectrum.ieee.org/feeds/feed.rss```

[Quanta Magazie](https://www.quantamagazine.org/)```https://api.quantamagazine.org/feed)```
