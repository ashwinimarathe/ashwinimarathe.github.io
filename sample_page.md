## This can be your internal website page / project page

**Project description:** This project aims to understand the features that hit songs have in common. In particular, I was interested in knowing if a song’s artist, the genre of the song and, its other musical features like danceability, energy, loudness among others can help distinguish hit and non-hit songs. To achieve this, I trained a logitistic regression model and compared the results of this model with the non-parametric classification method, random forests. Since the logistic regression model is more interpretable, I have drawn inferences from it. From the model, it can inferred that the popularity of a song’s artist and the song genre does highly influence the odds of a song getting hit. Another influential music feature is danceability. Songs that are more danceable have higher odds of becoming hit.

### 1. Data Collection method

To do this analysis I collected data from the [Spotify web-developer API](https://developer.spotify.com/) Spotify has a lot of data, but has rate cap on the APIs which is 10k for almost all APIs. This restricts the data collection and might introduce some bias as we are not aware which 10k song entries the API fetches. To mitigate this, I selected random genres and downloaded songs from last year. Using the Spotify API is relatively straightforward, however the time I soent in data collection was huge. So the repository has a csv of the data I collected and can be used to avoid all the tedious process of data collection.

```javascript
fetch("https://api.spotify.com/v1/audio-analysis/6EJiVf7U0p1BBfs0qqeb1f", {
  method: "GET",
  headers: {
    Authorization: `Bearer ${userAccessToken}`     
  }
})
.then(response => response.json())
.then(({beats})) => {
  beats.forEach((beat, index) => {
    console.log(`Beat ${index} starts at ${beat.start}`);
  })
}
```

### 2. Data Features

Spotify provides music related features for all songs on it's platform. These features include *acousticness*, *danceability*, *energy* and 11 more. I also wanted to analyze the effect of artist popularity and hence for artist's of all songs I collected information regarding the artist's popularity.

```javascript
curl -X GET "https://api.spotify.com/v1/artists/0OdUWJ0sBjDrqHygGUXeCF" -H "Authorization: Bearer {your access token}"
}
```

### 3. Data Visualization

I created a RShiny app to visualize different features of data. The RShiny app is hosted [here](https://ashwinimarathe.shinyapps.io/musicvisualization/)

<img src="images/rshiny.png?raw=true"/>

### 4. Model

I trained two models on the data, a logitic regression model to make inferences about the features affecting the popularity of songs. I also trained a Random Forest model and achieved accuracy of 95%. The notebook for modelling can be found [here](https://github.com/ashwinimarathe/Spotify-Song-Popularity-Prediction)

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
