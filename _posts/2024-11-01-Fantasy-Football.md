---
layout: post
title:  "A Fantasy Football Fantasy?"
author: Kolby Taylor
description: Are older running backs really taboo in fantasy football? Let's try and bust this myth together. 
image: "/assets/images/henry_stiff_arm.jpeg"


---
<div style="text-align: center;">
  <!-- Main image -->
  <img src="https://media.bleacherreport.com/image/upload/w_800,h_533,c_fill/v1730990862/uoirhdibr8qhhbpyvduj.jpg" alt="Saquon Barkley Hurdle" style="max-width: 800px; width: 100%; height: auto;">

  <!-- Link to YouTube video -->
  <p style="margin-top: 20px;">
    <a href="https://www.youtube.com/watch?v=qha5Sjamgr0" target="_blank" rel="noopener noreferrer">
      Watch Saquon Barkley's incredible hurdle on YouTube
    </a>
  </p>
</div>

## Not Worth the Money
When NFL running backs reach the end of their rookie contracts, most teams are too scared to pay them the big money that comes with a second. Since they're running into crowds of 300 pound linemen all the time,

Snubbed. Forgotten. Ignored. That’s probably how many top NFL players feel when their teams won’t pay them another contract. Last year, many teams refused to pay the top dollar to star running backs. Derrick Henry, Saquon Barkley, Joe Mixon, and Aaron Jones, some of the biggest stars in the league, all had to find new teams to play for.

```python
# Define base URL and parameters
base_url = "https://www.footballguys.com/playerhistoricalstats?pos={position}&yr={year}&startwk=1&stopwk=17&profile=p"
positions = ["qb", "rb", "wr", "te"]  # Add other positions as needed
years = range(2000, 2025)  # Loop from 2000 to the current year

# Initialize an empty list to store the data
all_data = []

# Loop through each position and year
for position in positions:
    for year in years:
        url = base_url.format(position=position, year=year)
        response = requests.get(url)
        soup = BeautifulSoup(response.content, "html.parser")
        
        # Find the table and extract data
        table = soup.find("table", class_="datasmall table")
        if table:  # Ensure the table exists
            # Extract headers
            headers = [header.text.strip() for header in table.find_all("th")]
            headers = ["Year", "Position"] + headers  # Prepend Year and Position
            
            # Extract rows
            rows = table.find_all("tr")
            for row in rows:
                cells = row.find_all("td")
                if cells:  # Ensure there are cells to extract
                    # Create a dictionary for the row
                    row_data = {
                        "Year": year,
                        "Position": position,
                        **{headers[i + 2]: cell.text.strip() for i, cell in enumerate(cells)}
                    }
                    all_data.append(row_data)
        else:
            print(f"No data found for {position} in {year}.")
```

NFL general managers weren’t the only ones afraid to trust these players. Anybody who plays fantasy football knows that older running backs were drafted way lower than they should have been. What were we afraid of? Old age? Injuries? Whatever it was, those fears have definitely not panned out. Just take a look at the top 5 running backs so far this year:
1.	Derrick Henry (30)
2.	Alvin Kamara (29)
3.	Bijan Robinson (22)
4.	Saquon Barkley (27)
5.	Chuba Hubbard (25)

Running back is a position that gets lots of wear and tear. They run hard and get tackled frequently by 300-pound linemen. Typically, teams don’t like to use them after five or so years in the league. This year, we’re seeing a huge buck in this trend. So, what’s the deal? Is it true that running back hit a wall in their mid-twenties? Let’s take a look and see if we can get to the bottom of this fantasy football fantasy.
Before we try and bust this myth, we need to find some data. For this problem I found an awesome website called footballguys.com. (Screenshot of website)
As you can see, the data’s all here, nice and organized. However, it would be a real pain to try and go through all the different dropdown arrows and try and copy the data page by page. Instead of doing this, we can use a basic web scraping method. By using Beautiful Soup, we can easily loop through all the tables that we need and get them into a nice dataset.
(Insert table that has top 10 running backs in each year with drop downs)
(Average age of top 10 running backs over the past 25 years)
(Injuries)
(Recommendations for next year)
