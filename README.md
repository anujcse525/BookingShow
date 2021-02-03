# BookingShow
Assignment

TASK:
❖ Create a web application to list movies available for a user.
❖ User should be able to search through the movies using the title and sort the result.
❖ When a selection is made it should go to the details page and present all the information
available for that movie(Plot, Ratings, Poster, Stills etc). The user should be able to go back
to the main page as well.
❖ There should also be a dedicated filter for the movies by Language or Location (drop down).

Movie Sample:
{
  "Language": "ENGLISH",
  "Location": "DELHI",
  "Plot": "Two imprisoned men bond over a number of years, finding solace and eventual redemption th
            rough acts of common decency.", "Poster": "https://m.media-
            amazon.com/images/M/MV5BMDFkYTc0MGEtZmNhMC00ZDIzLWFmNTEtODM1ZmRlYWMwMWFmXkEyXkFqcGdeQXVyMTMxODk2OTU@._ V1_QL50_.jpg",
   "SoundEffects": [ "RX6",
                     "SDDS"
                   ],
   "Stills": [
            "https://m.media- amazon.com/images/M/MV5BNTYxOTYyMzE3NV5BMl5BanBnXkFtZTcwOTMxNDY3Mw@@._V1_UY99_CR24,0,99,99_AL_.jpg",
            "https://m.media-
                    amazon.com/images/M/MV5BNzAwOTk3MDg5MV5BMl5BanBnXkFtZTcwNjQxNDY3Mw@@._V1_UY99_CR29,0,99,99_AL_.jpg",
            "https://m.media-
                    amazon.com/images/M/MV5BMDFkYTc0MGEtZmNhMC00ZDIzLWFmNTEtODM1ZmRlYWMwMWFmXkEyXkFqcGdeQXVyMTMxODk2OTU@._ V1_UX182_CR0,0,182,268_AL__QL50.jpg"
            ],
    "Title": "The Shawshank Redemption",
    "imdbID": "tt0111161",
    "listingType": "NOW_SHOWING",
    "imdbRating": "9.2"
}

Archicture:
Added Architecture diagram.

Start Of the Project:
1. Install time Postgres DB password will be created and stored in the vault server.
2. Application will read the password from Vault server.
3. Using Manticoresearch to make a fast search of movies and typeahead feature to search a movie.
4. Indexer of ManticoreSearch will be scheduled to run every 5 mins to read data from DB and store into the indices.
5. Frontend will be sending request to backend through Nginx(API gateway).
6. Nginx will verify the certificate and send request to Backend.
7. Backend will authenticate the user using OAuth2.
8. After verifying the request Backend will send the Access Token to the user, which will be used iin further requests.
9. To get the list of movies frontend will be using api /api/v1/movies -- Response will be in paginated form with self link
10. To Get the details of a movie frontend will be using /api/v1/movieDetails/{moviesName}
