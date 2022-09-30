---
title: "Aethra."
date: 2022-09-16T00:48:00Z
draft: false
toc: false
tags:
  - Technology
  - OSINT
  - Creating
---
On a sunny day, earlier this year, I left my flat and headed into town. This had become somewhat of a routine for me; go into the town centre, grab a drink and go for a stroll. It keeps me happy. I sat down in the kind of chain cafè that only really exists in the UK and took out the book I had been reading. "We are Bellingcat" by Elliot Higgins is an almost autobiographical book that explains how Higgins and a growing group of followers and friends started Bellingcat and created the ever-growing field of Open Source Intelligence or OSINT. On that particular day, I was just finishing that book when I read something that struck me.

Higgins, at the end of his book, explains that the field is ever expanding and really needs new tools to increase the capability of investigators, geolocators and journalists. There are ever-increasing demands on the field to investigate and uncover the atrocities and tactics of wars and despots around the world. He writes: "In future, we hope to combine the efforts of volunteers with the might of machine learning. For instance, if Bellingcat identified a YouTube video containing a valuable piece of evidence [...] AI might comb through a vast dataset of other videos for similar footage, producing a list of several hundred clips."

This instantly made me think of the work I had been doing in the months before that. At the beginning of this year, I had noticed, like many others, the heavy accumulation of Russian troops and forces just beyond the borders of Ukraine. I thought that it might perhaps be useful if other OSINT-ers and investigators had access to the history of military vehicles and weapons, so I started to imagine and build a database that might aid in this. Eventually, however, after Russia did invade, I realised that this effort was largely futile and perhaps entirely pointless. There were so many Russian vehicles and weapons and so few massacres being investigated in the kind of detail that required knowing the specific weapon used.

When I finished this book, however, on that spring day, I realised that there was another kind of database that might be much more impactful. A database that held the history of online videos. If you found a video online, as I had been doing for months, and wanted to know where it came from; then that was a long and laborious task that would probably require hours of painstaking re-tracing of where people had found and re-posted that clip. For images, however, there was a simpler solution: take your image to google images, paste the link and voilà, you had practically everywhere that image had been seen on the internet right in front of you.

But immediately I knew that the same was more than possible for video; it just hadn't been done yet. More than that, I knew that as a first-year Computer Science student who had been programming for a few years already and had just been learning database design; I knew that I could do it. That very afternoon, I sketched out a plan. It would need 2 main constituent parts; a crawler (A piece of code that trawls the depths of the internet, in this case looking for videos and storing them in a database) and a website to search and display the contents of the database: if this tool was to be used, it needed to be easy.

In the following weeks, I got to work. I started by creating the crawler, I could set it to work while I worked on the website. One of the things I had known immediately was that I could use something called a "hashing algorithm" to create a kind of fingerprint which would let me compare different videos to see if they were the same or similar. This meant that I didn't even necessarily need AI as Higgins had suggested. I knew this could be done and as it turned out, it already had been. I found a python package which would let you create a hash of any video based on a downloaded version, or a URL. This proved very useful as I could pretty much skip the most complicated part of this project for the time being and get on with making my "Minimum Viable Product". I realised that this would likely not be the most perfect version of such an algorithm for my needs but it will have to do until I have the time to improve on it.

The crawler would then go around looking for videos, hash them and look at the database, comparing hashes to see if that video had ever been seen before. If it hasn't it will add that hash to the database. One of the most important techniques that I have employed here is that of a "Binary search". This method of searching allows me to make sure that the time it takes to find something in the database doesn't scale linearly with the size of the database. So as the database grows bigger, the time it takes to search it grows much more slowly; or rather logarithmically.

For those who know Big O notation:

Binary search = `O(log(N))` while Linear search = `O(N)`

The search function on the web side works much the same way, although, at the time of writing, this has yet to be made particularly efficient.

I have yet to expand the range of the crawler; I expect soon to be able to add TikTok, telegram and a host of other platforms in order to be able to support the work of OSINT investigators large or small. For the time being, I'm only using a simple crawling method on Twitter that only really catches a number of the most prominent video sources, this also largely focuses on Ukraine at the moment.

I am also planning on adding the posts that I crawl to the Internet Archive in order to make sure that they remain available even if the post itself is removed. This would allow people to gain an even better understanding of the way in which these videos have spread / where they really come from.

The best part for me about this project is that so far I've managed to keep it free. I can keep it this way until I get to around a million videos in the database after which I will have to start paying for storage. I have also created a page for donations if people would like to support my work.

Lastly, I have also thought about creating an API for the database, this should be relatively easy if there is demand for this but I'm not sure I see a use case for this. If someone would be interested in that, feel free to contact me.

The website is [**Aethra.Video**](https://Aethra.video/).

-- Chico Demmenie.

[Re-Uploaded & Edited 30/09/2022]
