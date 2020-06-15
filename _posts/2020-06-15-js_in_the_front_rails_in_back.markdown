---
layout: post
title:      "JS in the front Rails in back"
date:       2020-06-15 19:06:39 +0000
permalink:  js_in_the_front_rails_in_back
---


In this blog I would like to discuss an important topic (and possibly one of the more challenging) when working on a small project using *JavaScript* to communicate with a backend API built with *Ruby on Rails*. 

It is the FETCH API  which "*provides a JavaScript interface for accessing and manipulating parts of the HTTP pipeline, such as requests and responses. It also provides a global fetch() method that provides an easy, logical way to fetch resources asynchronously across the network.*"-[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

To examine and discuss how this works we will look at code from my JavaScript and Rails Project.

GET
```javascript
function getSongs() {
        fetch(songEndPoint)
        //the simplet GET fetch takes just the path to the resource you want to fetch
        .then(response => response.json())
        //this returns the response object/promise which needs to be extracted to JSON using the json() method
        .then(songs => {
          songs.data.forEach(song => {
            //double check how your data is nested in the console so you can access the attributes of each individual object
            
        
            let newSong = new Song(song, song.attributes)
            //I then use this nested data to created instances of my Song class and manipulate the DOM
            document.querySelector('#song-container').innerHTML += newSong.renderSongCard()
          })
        .catch(err => console.log(err))
        })
      }
```


POST
```javascript
   function postFetch(name, lyrics, chords, category_id){
        let formData = {name, lyrics, chords, category_id}
        //data we want to send in body, in an object
        let configObj = {
            method: "POST",
            //we need to change to default GET to POST
            headers: {
                "Content-Type": "application/json",
                "Accept": "application/json"
                //headers say what data we are sending and what we'd like to recieve
            },
            body: JSON.stringify(formData)
            //the data we want to send is converted into a string using this built in method
        }
        fetch(songEndPoint, configObj)
        //fetch then takes 2 arguments 1.the path 2.our configObj with all of the data and metadata we need to give to the server
        .then(response => response.json())
        .then(song => {
         //the server returns the newly created song object and we append it to the DOM 
            const songData = song.data
            let newSong = new Song(songData, songData.attributes)

            document.querySelector('#song-container').innerHTML += newSong.renderSongCard()
            

        })
        .catch(err => console.log(err))
    } 
    ```
    
    PATCH
    ```javascript
    function patchFetch(name, lyrics, chords, category_id, id){
        let formData = {name, lyrics, chords, category_id}

        let configObj = {
            method: "PATCH",
            // just the path and the method is changed
            headers: {"Content-Type": "application/json"},
            body: JSON.stringify(formData)
        }
        
        fetch(`http://localhost:3000/api/v1/songs/${id}`, configObj)
        .then(response => response.json())
        .then(song => {
            console.log(song)
        })
        .catch(err => console.log(err))
        
    }
    ```
    
    So there you have it. GET, POST, and PATCH using fetch().  In summary fetch can take 1 or two arguments.  Makes sure you are using the correct path and method to your desired resource contained in your Rails API backend.  To recieve and handle any errors make sure you implement a catch at the end of your fetch request.  Finally, creating a configuration object containing your headers, body and method can clean up your code.

