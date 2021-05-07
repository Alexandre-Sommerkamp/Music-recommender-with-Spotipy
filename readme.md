![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Lab | API wrappers - Create your collection of songs & audio features


# Case Study: The site for recommendations - "Gnod"

### Scenario

You have been hired as a Data Analyst for "Gnod".

"Gnod" is a site that provides recommendations for music, art, literature and products based on collaborative filtering algorithms. Their flagship product is the _music recommender_, which you can try at [www.gnoosic.com](www.gnoosic.com). The site asks users to input 3 bands they like, and computes similarity scores with the rest of the users. Then, they recommend to the user bands that users with similar tastes have picked.

"Gnod" is a small company, and its only revenue stream so far are adds in the site. In the future, they would like to explore partnership options with music apps (such as _Deezer_, _Soundcloud_ or even _Apple Music_ and _Spotify_). However, for that to be possible, they need to expand and improve their recommendations.

That's precisely where you come. They have hired you as a Data Analyst, and they expect you to bring a mix of technical expertise and business mindset to the table.

Jane, CTO of Gnod, has sent you an email assigning you with your first task.

### Task(s)

> This is an e-mail Jane - CTO of Gnod - sent over your inbox in the first weeks working there.

_Dear xxxxxxxx,
We are thrilled to welcome you as a Data Analyst for *Gnoosic*!_

_As you know, we are trying to come up with ways to enhance our music recommendations. One of the new features we'd like to research is to recommend songs (not only bands). We're also aware of the limitations of our collaborative filtering algorithms, and would like to give users two new possibilities when searching for recommendations:_

- _Songs that are actually similar to the ones they picked from an acoustic point of view._
- _Songs that are popular around the world right now, independently from their tastes._

_Coming up with the perfect song recommender will take us months - no need to stress out too much. In this first week, we want you to explore new data sources for songs. The Internet is full of information and our first step is to acquire it do an initial exploration. Feel free to use APIs or directly scrape the web to collect as much information as possible from popular songs. Eventually, we'll need to collect data from millions of songs, but we can start with a few hundreds or thousands from each source and see if the collected features are useful._

_Once the data is collected, we want you to create clusters of songs that are similar to each other. The idea is that if a user inputs a song from one group, we'll prioritize giving them recommendations of songs from that same group._

_On Friday, you will present your work to me and Marek, the CEO and founder. Full disclosure: I need you to be very convincing about this whole song-recommender, as this has been my personal push and the main reason we hired you for!_

_Be open minded about this process: we are agile, and that means that we define our products and features on-the-go, while exploring the tools and the data that's available to us. We'd love you to provide your own vision of the product and the next steps to be taken._

_Lots of luck and strength for this first week with us!_

_-Jane_

### Execution: Labs

#### Day 1: Scraping popular songs

Your product will take a song as an input from the user and will output another song (the recommendation). In most cases, the recommended song will have to be similar to the inputted song, but the CTO thinks that if the song is on the top charts at the moment, the user will enjoy more a recommendation of a song that's also popular at the moment.

You have find data on the internet about currently popular songs. Billboard maintains a weekly Top 100 of "hot" songs here: [https://www.billboard.com/charts/hot-100](https://www.billboard.com/charts/hot-100).

It's a good place to start! Scrape the current top 100 songs and their respective artists, and put the information into a pandas dataframe.

#### Day 2: Prioritize the MVP

In the previous lab, you had to scrape data about "hot songs". It's critical to be on track with that part, as it was part of the request from the CTO.


#### Day 2(extra): Practice web scraping  and make a multiple page scraping

As you've seen, scraping the internet is a skill that can get you all sorts of information. Here are some little challenges that you can try to gain more experience in the field:

- Retrieve an arbitrary Wikipedia page of "Python" and create a list of links on that page: `url ='https://en.wikipedia.org/wiki/Python'`
- Find the number of titles that have changed in the United States Code since its last release point: `url = 'http://uscode.house.gov/download/download.shtml'`
- Create a Python list with the top ten FBI's Most Wanted names: `url = 'https://www.fbi.gov/wanted/topten'`
- Display the 20 latest earthquakes info (date, time, latitude, longitude and region name) by the EMSC as a pandas dataframe: `url = 'https://www.emsc-csem.org/Earthquake/'`
- List all language names and number of related articles in the order they appear in [wikipedia.org](wikipedia.org): `url = 'https://www.wikipedia.org/'`
- A list with the different kind of datasets available in [data.gov.uk](data.gov.uk): `url = 'https://data.gov.uk/'`
- Display the top 10 languages by number of native speakers stored in a pandas dataframe: `url = 'https://en.wikipedia.org/wiki/List_of_languages_by_number_of_native_speakers'`

#### Day 3: API Wrappers 

To move forward with the project, you need to create a collection of songs with their audio features - as large as possible! 

These are the songs that we will cluster. And, later, when the user inputs a song, we will find the cluster to which the song belongs and recommend a song from the same cluster.
The more songs you have, the more accurate and diverse recommendations you'll be able to give. Although... you might want to make sure the collected songs are "curated" in a certain way. Try to find playlists of songs that are diverse, but also that meet certain standards.

The process of sending hundreds or thousands of requests can take some time - it's normal if you have to wait a few minutes (or, if you're ambitious, even hours) to get all the data you need.

An idea for collecting as many songs as possible is to start with all the songs of a big, diverse playlist and then go to every artist present in the playlist and grab every song of every album of that artist. The amount of songs you'll be collecting per playlist will grow exponentially!

#### Day 4: Unsupervised Learning 

It's the moment to perform clustering on the songs you collected. Remember that the ultimate goal of this little project is to improve the recommendations of artists. Clustering the songs will allow the recommendation system to limit the scope of the recommendations to only songs that belong to the same cluster - songs with similar audio 
features.

The experiments you did with the `Spotify` API and the Billboard web scraping will allow you to create a pipeline such that when the user enters a song, you:

1. Check whether or not the song is in the Billboard Hot 200.
2. Collect the audio features from the `Spotify` API.

After that, you want to send the `Spotify` audio features of the submitted song to the clustering model, which should return a cluster number.
If you want to have even more songs in addition to the ones you already collected, you can add songs from a [dataset available on Kaggle containing 130k songs.](https://www.kaggle.com/tomigelo/spotify-audio-features)