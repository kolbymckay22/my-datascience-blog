---
layout: post
title:  "A Fantasy Football Fantasy?"
author: Kolby Taylor
description: Are older running backs really taboo in fantasy football? Let's try and bust this myth together. 
image: "/assets/images/henry_stiff_arm.jpeg"


---
<div style="text-align: center;">
  <img src="https://media.video-cdn.espn.com/motion/2024/1113/dm_241113_ffp_joe_mixon/dm_241113_ffp_joe_mixon.jpg" alt="Joe Mixon" style="max-width: 800px; width: 100%; height: auto;">
</div>


## Not Worth the Money
When NFL running backs reach the end of their rookie contracts, most teams are too scared to pay them the big money that comes with a second contract. Since running backs crash into crowds of 300 pound linemen all the time, they often get hurt, wear down, and end up running out of steam early in their careers.

NFL general managers weren’t the only ones afraid to trust these players. Anybody who plays fantasy football knows that older running backs were drafted way lower than they should have been. What were we afraid of? Old age? Injuries? Whatever it was, those fears have definitely not panned out.

## Proving Everyone Wrong
Last year, many teams refused to pay top dollar to their star running backs. Derrick Henry, Saquon Barkley, and many other star running backs had to find new teams to play for. And boy, it really seems like they're trying to prove everybody wrong. This year, we've seen total domination from these resurging stars. Just check out this incredible hurdle Saquon Barkley threw down a couple of weeks ago.


<div style="text-align: center;">
  <img src="https://media.bleacherreport.com/image/upload/w_800,h_533,c_fill/v1730990862/uoirhdibr8qhhbpyvduj.jpg" alt="Saquon Barkley Hurdle" style="max-width: 800px; width: 100%; height: auto;">
  <p style="margin-top: 20px;">
    <a href="https://www.youtube.com/watch?v=qha5Sjamgr0" target="_blank" rel="noopener noreferrer">
      Watch Saquon Barkley's Incredible Hurdle
    </a>
  </p>
</div>


If so many older running backs are having success this year, then why aren't teams paying them? Why aren't they being drafted in fantasy football? Are missing something? Let's take a look at the data and see if we can figure out if older running backs truly are too risky to draft.

## Diving into the Data
To do this analysis, I'm going to web scrape data from a website called [Fantasy Football Guys](https://www.footballguys.com/playerhistoricalstats?pos=rb&yr=2023&startwk=1&stopwk=17&profile=p). You should check it out! They have awesome data on fantasy football going all the way back to the 90's. Remember, if you want to web scrape this website or any other, make sure to look for possible policies about what you're allowed to do with the data. Many websites ban web scraping. I looked for a robots.txt file and read their privacy policy, but couldn't find anything prohibiting web scraping, so we're good to go! I scraped and tidied my data in another file, so it's good to go for us to use.

```python
# Import pandas
import pandas as pd

# Read the fantasy.csv data into a DataFrame
fantasy_df = pd.read_csv('fantasy.csv')

# Display the first few rows of the data
fantasy_df.head(5)
```

(Insert table that has top 10 running backs in each year with drop downs)
(Average age of top 10 running backs over the past 25 years)
(Injuries)
(Recommendations for next year)
