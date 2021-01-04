---
title: What I Use Now Instead Of Google
date: 2021-01-03
---

I made a goal for myself in January 2020 to stop using Google products by the end of the year. That might sound like way too generous a timeline, but Google owned pretty much all of my data at that point, so it was a fairly large project. Plus I'm a slow and steady kind of person. I know if I give myself a generous enough timeline I can accomplish even things that seem too hard for me at first.

## But Why

Since I got into programming about 5 years ago, I kept hearing all these bad things about Google and how horrible of a company it is from other tech people. It always seemed a bit superfluous, but the evidence been piling up over the years. Learning about [their involvement](https://gizmodo.com/google-is-helping-the-pentagon-build-ai-for-drones-1823464533) with the US military's [Algorithmic Warfare Cross-Functional Team (Project Maven)](https://dodcio.defense.gov/Portals/0/Documents/Project%20Maven%20DSD%20Memo%2020170425.pdf) was the last straw for me, but even before I learned about that I was pretty uncomfortable with a lot of what I heard. That last link goes to a memo saying that the primary purpose of the project is "to field technology to augment or automate Processing, Exploitation, and Dissemination (PED) for tactical Unmanned Aerial System (UAS)", which means making AI for drones so they can better target humans and other "targets". Not ok by me. Very not ok. In Google's defence they eventually did [pull out of the project](https://web.archive.org/web/20210101083904/https://www.nytimes.com/2018/06/01/technology/google-pentagon-project-maven.html) after [massive backlash by thousands of employees](https://web.archive.org/web/20201231204850/https://www.nytimes.com/2018/04/04/technology/google-letter-ceo-pentagon-project.html). 

Still, I'm pretty convinced now that their continued existence is a catastrophe not only for public safety, but also for [the environment](https://www.vox.com/recode/2020/1/3/21030688/google-amazon-ai-oil-gas), [gender equity](https://www.nytimes.com/2018/11/01/technology/google-walkout-sexual-harassment.html), [the economy](https://www.telegraph.co.uk/technology/google/9739039/Googles-tax-avoidance-is-called-capitalism-says-chairman-Eric-Schmidt.html), [fair labour practices](https://www.vice.com/en/article/jgexe8/google-fired-an-engineer-who-wrote-code-telling-googlers-they-had-a-right-to-organize), [privacy](https://www.stallman.org/google.html#surveillance), [journalism](https://www.nature.com/articles/s41562-020-00954-0), [democracy](https://www.judiciary.senate.gov/download/epstein-testimony), [race relations](https://www.vox.com/2018/4/3/17168256/google-racism-algorithms-technology), and the [project of civilization itself](https://www.scientificamerican.com/article/big-tech-out-of-control-capitalism-and-the-end-of-civilization/). But anyway, the point of this post isn't to motivate you to also quit Google. I'll tell you how I really feel some other time.

The title suggests this is a post about what products are available to replace Google, which it is what the rest of this is about. These are the tools and services I use now.

## Replacements

Here is the compendium of products I switched to in my quest to stop using Google. I did accomplish my goal, with some caveats which I describe in each section, if relevant.

### GMail -> [ProtonMai](https://protonmail.com/signup)

ProtonMail has free accounts, but I pay for the lowest level that allows use of a custom domain with it (€48/year) so I don't have to change my email address ever again if I want to switch providers. It was quite a pain to change my email address all over the place, but I started in May this year and just did it slowly over time. I highly recommend decoupling your email address from your email provider if you're considering switching away from Google. First of all an email from a custom domain seems more, not less, serious than a gmail address to most people. But the main reason is just so you don't have to change your email address ever again and more and better email providers come online.

I set up forwarding from my old GMail account to my new email address then filtered my mail for anything sent to the old address. If it was someone or some place I wanted to continue hearing from, I updated my email address with them. If not I unsubscribed. This turned out to be a wonderful opportunity to purge my newsletter and other email subscriptions. Also I'm happy to report most companies are now (finally) respecting unsubscribe requests. Only one continued to send me email after I asked them not to, so I manually set up a rule in my inbox to send anything from them directly to trash.

### Chrome -> Firefox developer edition

I primarily use [Firefox developer edition](https://www.mozilla.org/en-US/firefox/developer/) now for my browser, including for work. The developer tools are just as good as Chrome's for the kind of work I do.

There are some web apps that literally or effectively only work in Chrome, which ironically perfectly illustrates the impetus for this project. For those I use this [ungoogled Chromium](https://github.com/Eloston/ungoogled-chromium#downloads) browser, installed via homebrew.

I still have Chrome installed on my computer because I need it for some work things. We use chromedriver for some integration tests and it wasn't trivially easy to trick it into using my Chromium installation instead of looking for Chrome. Replacing chromedriver is a headache, and also not my call to make at work. But it's also not really the point for me. If google was reduced to a browser that developers can easily launch and control programmatically, I'd be satisfied.

### Google search -> [DuckDuckGo](duckduckgo.com)

Honestly DuckDuckGo results are often not as good as Google's for certain kinds of searches. It doesn't seem to return results form forums (like stack overflow or other stack exchange sites), which is what I'm looking for most of the time. So I still use Google Search sometimes, but I at least do it in a [Firefox container](https://addons.mozilla.org/en-US/firefox/addon/multi-account-containers/) without being logged in to a Google account.

DuckDuckGo does seem to return better results when the answer is an image, video, or regular web page, which is cool, and I suspect means it would be a perfectly fine replacement for most people. For example this blog is easier to find via DuckDuckGo than Google, which is impressive because I share a name with a small-time TV celebrity who typically dominates search results. We even look sort of similar, it's kind of weird.

### Google Drive -> [Sync](https://www.sync.com/) and [Backblaze](https://www.backblaze.com/b2/cloud-storage.html)

I use Sync to make my recent files available anywhere, and I've started moving a huge backlog of documents and notes I don't need to access often but don't want to throw away to Backblaze for longer term storage. So far I just use their web UI to upload things in bulk and browse my files, but I'm looking into ways to do that more efficiently. I'm also looking into ways to mount a Backblaze bucket as an folder on my computer so I can access my archives more easily for those rare times I want to.

Between Sync and Backblaze I got 15GB of free storage, which is plenty for now, though as I move more and more or my scattered files over I'll have to start paying. Backblaze offers some of the cheapest object storage there is, at least.

### Calendar, reminders, photos, docs, video chat, news feeds -> [Nextcloud](https://nextcloud.com/signup/)

For everything else I use Nextcloud now. I [run my own instance](/blog/how-to-set-up-your-own-nextcloud-server/) of it, but there are lots of providers where you can just sign up for a simple account like anything else if you're not an insufferable nerd who enjoys that kind of thing, like me.

This is where I have another caveat to mention. I haven't migrated all of my photos off of Google photos yet because I have about 50 thousand of them and it's just a really slow process. I estimated it would take me something like 70 hours to move them all manually, so I'm looking into better ways to do it. I'm confident I can build something easier than manually downloading and uploading 50k files in less than 70 hours.

Nextcloud does the job of automatically syncing photos from my phone, though, which is all I needed to be able to delete Google Photos from my devices. I'm not sure I'll actually stick with Nextcloud for photos in the long run. The gallery is a bit lacking. It looks like [Piwigo](https://piwigo.org/get-piwigo) might be a good alternative. Either way, I'm actually storing my photos in Backblaze, so I'll continue looking around for a different client for a bucket full of photos next year.

### DNS -> Cloudflare DNS

I used to use Google's DNS servers (8.8.8.8 and 8.8.4.4), now I use (Cloudflare's)[https://blog.cloudflare.com/announcing-1111/] (1.1.1.1 and 1.0.0.1).

### Maps, YouTube

These ones are harder to replace. I use Apple maps now most of the time, but I still use Waze (which was acquired by Google) for directions sometimes. For media I mostly watch netflix, but also find lots of great talks on ted.com

### Analytics -> [Fathom](https://usefathom.com/)

Fathom provides simple privacy-focused analytics that work well enough for me. One really useful feature they have that I consider necessary now is being able to log analytics with a custom domain. Without this, visitors using ad-blockers don't get counted, which most estimates figure is now something like 40% of people, and probably more among tech-type people, like the ones most likely to find this blog. I tried cloudflare's new server-side analytics for a month, but the data didn't make as much sense (it showed the overwhelming number of visits to my homepage, even though the other analytics I had set up showed them going to one post that did well on Hacker News, which makes way more sense). Anyway, the numbers didn't seem to add up. I guess to be fair I don't quite understand how Fathom's numbers add up yet either [quote tweet], but their support has been really helpful checking it out with me to try to help me reach some interpretation that makes sense. Fathom's dashboard is really simple, though, which I like, and they can also email you periodically with an overview of your website stats for the week (or whatever), which is also nice.

## Total Cost

I feel like I've won a lot by doing all this. I own my data now, so Google can't arbitrarily take it away from me or start charging me for access to it, which gives me peace of mind. I'm no longer part of their ad ecosystem, being tracked all around the internet and having my attention sold to the highest bidder. And I also feel good about "voting with me feet", so to speak. The fewer people use Google's free products, the lower their ability to sustain their unethical business model.

But I also lost some. Mainly a few hundred dollars.

Getting paid and paying for things in multiple currencies is the bane of my financial existence, but that works out to roughly something like CAD$375/year.

ProtonMail - €48/year ($75)
Custom domains - $19.74/year ($25)
Carbon offsets - CAD$21/year
Linode server - $60/year ($75)
Fathom analytics - $140/year ($180)

As you can see, analytics costs me a fair amount. I thought about setting up a simple server to just count page views myself, but I already shaved about a thousand yaks to get this website up and running so I'm happy to just pay for analytics for now.

Once I got over the initial hurdle of expecting everything to be free or as cheap as possible, this seemed like a totally reasonable amount to pay for all I'm getting. What made it click for me is that all those things aren't actually free. Google sells your information and your attention to the highest bidder to generate profit for themselves, and they don't share any of it with you, despite the fact that their entire business model couldn't even exist if we all just refused to fuel it. 
