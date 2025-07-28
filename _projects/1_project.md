---
layout: page
title: Timbre
description: a “music social media” that connects users with similiar music tastes
img: assets/img/timbre/background.png
importance: 1
category: development
---
This project is the senior capstone completed to fulfill the rqeuirement for bachelor's in data science and analytics from CWRU. 

__Skills & Tools invovled:__ Python, Javascript, PostgreSQL, Node.js, React, Algorithm Design, Data Processing

Timbre works with existing music services to fill a gap by providing a solution for music social media. Most music streaming services recommend music primarily based on the music that someone has listened to, but Timbre differs by providing recommendations based on the music that other people with similar preferences recommend, which combines both a data science approach with a social media aspect.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/timbre/background.png" title="login image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 1. Login Screen
</div>

The front-end and middleware is built using Next.js, a React based full-stack framework, and the backend database is hosted on PostgreSQL, a relational database management system. Our group consists of 5 members and I primarily worked on the backend and middleware to
- design and implement the database
- develop and optimize compatibility score calculation
- formulate user-matching procedure and algorithm 
- integrate SQL and javascript functions to process frontend requests

### Database Design
Timbre’s relational database is implemented and hosted on PostgreSQL, with a schema of nine tables covering users, songs, ratings, music characteristics, and social features like friendships and recommendations. User preferences are modeled using Spotify listening data, stored in the `song_profile` table with features like valence, danceability, and loudness.

To support personalized recommendations and social matching, we track song ratings and compatibility between users. The database includes stored procedures and functions (e.g., `make_rating`, `get_top_ratings`) to manage and retrieve data efficiently, with security privileges in place to control access.

The design evolved alongside the project, adapting to new features and user needs. See the ER diagram below for the full schema.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/timbre/database.png" title="ERD database" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 2. ER diagram
</div>

### Matching Algorithm
To measure music compatibility between users, we developed a scoring system based on Spotify audio features. We use nine key attributes provided by Spotify's API for each track - scaled between 0 and 1 - to represent a user’s music taste:

- _Danceability, Energy, Loudness, Speechiness, Acousticness, Instrumentalness, Liveness, Valence, and Tempo_

For each user, we aggregate songs across four categories, each contributing differently to the final compatibility score:

- 30% – Top 10 user-rated songs (weighted by rating)
- 30% – Top 10 Spotify songs (weighted by ranking)
- 20% – 15 Recently played songs (unweighted)
- 20% – Top 5 artists (5 songs per artist, artists weighted)

We calculate the average feature vectors for each category, then compute a weighted similarity score between users. The diagram below illustrates the full workflow from user input to compatibility output.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/timbre/workflow.png" title="Workflow Diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 3. Workflow from Input to Output
</div>

## Site Breakdown
The site can be broken down into four pages: home, matches, friends, and profile.

### Homepage

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timbre/homepage_track.png" title="homepage image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timbre/homepage_search.png" title="searchbar image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 4. Homepage screen. Left: homepage with the search bar and top tracks of the user. Right: song view that allows one to play and rate the song upon clicking the track in the search bar or in the top tracks page.
</div>

This page provides the user's listening data and allows them to search and rate songs to help us improve their matches. Through Spotify API, we fetch user's recent tracks and display them on the homepage. Users can search for specific songs or artists and provide ratings. These ratings are then used to refine our matching algorithm, ensuring that future matches better align with the user's preference. Additionally, the page updates in real-time, whenever, the user logs in or resync with Spotify.

### Matches

This page displays a user’s top matches; that is, other Timbre users whom they have a high compatibility score with. The calculation process includes a random sampling approach to reduce runtime. In this method, a random small sample of users from the database is extracted(excluding the local user and any existing friends), to compute compatibility score between the local user and each of the randomly-sampled users. Scores are calculated based off user-specific song characteristics stored in the database.

The user is able to view their calculated compatibility score as well as information on the other user, including their Spotify profile picture, username, and bio. The user is then able to request to add these matches as friends. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timbre/matches_score.png" title="matchpage image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timbre/matches_bio.png" title="match bio image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 5. Matches screen. Left: matches page, with front-side cards showing the profile picture and display name, and the back-side card showing the compatibility score. Right: pressing the “Open Bio” allows the user to view each match’s bio text.
</div>

### Friends

This page serves as a hub for users to perform “social” actions, such as viewing, accepting, or denying their incoming friend requests, sending song recommendations to friends, and viewing recommendations they have received from others.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timbre/friends.png" title="friendpage image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timbre/song_rec_to.png" title="song recommendation to friend" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 6. Friends screen. Left: friend list, showing the compatibility scores, as well as the ability to recommend friends songs. Right: A search bar pops up that allows the user to recommend any song to their friends.
</div>

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 mx-auto">
        {% include figure.liquid loading="eager" path="assets/img/timbre/song_rec_from.png" title="friendpage image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 7. The recommendations screen allows users to view, play, and rate their song recommendations from other friends.
</div>

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 mx-auto">
        {% include figure.liquid loading="eager" path="assets/img/timbre/friend_request.png" title="friendpage image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 8. Requests screen. Top: A search bar allows the user to type in an email to send a friend request. Bottom: Incoming friend requests can be accepted and denied.
</div>

### Profile

This page displays a user's personal details, such as their display name and bio. They also have the ability to update and change their bio, which is what is displayed to other users when they are matched. Additionally, users can resync their Spotify accounts, which will trigger reauthentication; this will also trigger recalculation of song profiles and compatibility scores.

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 mx-auto">
        {% include figure.liquid loading="eager" path="assets/img/timbre/profile.png" title="friendpage image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 9. Profile screen, displaying user info and allowing update of the SQL database.
</div>
