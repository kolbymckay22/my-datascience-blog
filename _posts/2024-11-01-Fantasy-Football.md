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

## An Introduction to Web Scraping
To do this analysis, I'm going to web scrape data from a website called [Fantasy Football Guys](https://www.footballguys.com/playerhistoricalstats?pos=rb&yr=2023&startwk=1&stopwk=17&profile=p). You should check it out! They have awesome data on fantasy football going all the way back to the 90's. Remember, if you want to web scrape this website or any other, make sure to look for possible policies about what you're allowed to do with the data. Many websites ban web scraping. I looked for a robots.txt file and read their privacy policy, but couldn't find anything prohibiting web scraping, so we're good to go! I scraped and tidied my data in another file, so it's good to go for us to use.

The simplest way to scrape is to use a python package called Beautiful Soup. Essentially, Beautiful Soup turns the underlying code of the website into text, allowing us to use simple code to find tags in the html and extract the elements. I won't go into much detail here, but if you'd like to learn more, [here is a great repository with documenation on Beautiful Soup](https://tedboy.github.io/bs4_doc/) 

Here is the code I used to scrape my fantasy football data from Fantasy Football Guys:

``` python
# Define base URL
base_url = "https://www.footballguys.com/playerhistoricalstats?pos=rb&yr={year}&startwk=1&stopwk=17&profile=p"

# Specify the years we want to scrape
years = range(2000, 2025)

# Initialize an empty list to store the data
all_data = []

# Loop through each year
for year in years:
    url = base_url.format(year=year)
    response = requests.get(url)
    soup = BeautifulSoup(response.content, "html.parser")
    
    # Find the table and extract headers
    table = soup.find("table", class_="datasmall table")
    if table:
        headers = [header.text.strip() for header in table.find_all("th")]
        headers = ["Year"] + headers
        
        # Extract rows
        rows = table.find_all("tr")
        for row in rows:
            cells = row.find_all("td")
            row_data = {
                "Year": year,
                **{headers[i + 1]: cell.text.strip() for i, cell in enumerate(cells)}
            }
            all_data.append(row_data)
```

## Diving into the Data
The dataset shows every player and their stats going back to the year 2000. I didn't care too much about the specific stats, like touchdowns and yards. I particularly wanted to look at the age of the running back, how many years they had been in the league, how many games they played that season, their total points, and their average points per game. I also only wanted to look at relevant running backs. In other words, if a player was on the bench for his whole career, I didn't want his poor statistics throwing off the analysis. So, I kept only running backs who at some point in their career placed in the top 30.

``` python
# Identify running backs who have ever ranked 30 or less
rbs_with_top_rank = fantasy_df.groupby('Name')['Rank'].min()
top_rbs = rbs_with_top_rank[rbs_with_top_rank <= 30].index

# Filter the original DataFrame to keep only rows for these top running backs
fantasy_df_filtered = fantasy_df[fantasy_df['Name'].isin(top_rbs)]
```

Now that we have the data, we can dive into the question: Does age affect production? I'll only dive into a couple of points here, but if you're curious to know more, you can find my data and analysis in this [Github repository](https://github.com/kolbymckay22/Fantasy-Football-Analysis).

![Age Distribution of Top 10 Running Backs](https://raw.githubusercontent.com/kolbymckay22/my-datascience-blog/refs/heads/main/assets/images/age_distribution_of_top_10_rbs_plot.png)

First, let's see if the age of the top players at the position has changed over the years. The graph above shows how the distribution of ages in the top 10 running backs has changed over time. The general belief is that running backs typically decline when they're around 27 years old. In the graph, we can see that in the past, there were more older running backs over the age of 25. In general, it seems like they are disappearing more and more. So, is it true that older running backs aren't as good? And why are they worse now than they were twenty years ago?

Could it be injuries? It would make sense that with as running backs get older, they would start getting hurt more often and playing less games every season. Is it possible that they're good when they play, but because they don't play very often, they aren't as valuable? Let's look into it to find out. 

![Age Distribution of Top 10 Running Backs](https://raw.githubusercontent.com/kolbymckay22/my-datascience-blog/refs/heads/main/assets/images/average_points_and_games_played.png)

To look into this, we'll calculate the average games played and average fantasy points per game for each age of running backs. Looking at the graph, we can notice some interesting trends. It doesn't seem like injuries increase too much as the player gets older, at least not until they get into their mid thirties. However, the average points per game does seem to fall off pretty sharply once a running back hits 28 years olds.

## My Advice
Here are a few tips that you can use going into next year's fantasy football draft:
1. Injuries seem to be somewhat random. However, when drafting players, make sure you check and see if they have serious injury history in their past.
2. Don't be afraid to draft an older running back. There aren't many indicators that they fall off or get injured more often once reaching a certain age.
3. Focus on the situation! Coaching, success of the offense, and competition from other running backs on the team.

If you follow these tips, you're sure to have success next year! Well, no promises. Good luck drafting!