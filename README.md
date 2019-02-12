# Adventure Quest

## Parts

### index

* Allow user to choose a name
* Allow user to choose a race
* Save user information in `localStorage`
  * user has a `name`, `race`, `hp`, and `gold`

### map

* Display a list of all (uncompleted) quests
* Display current health
* Display current gold
* Check users current health
  * If health is less than or equal to 0 redirect to end

### quest

* Get the quest id from search query
* Find quest in quests array
* Display image for quest
* play audio for quest
* Display questions for quest
* On submit
  * update health
  * update gold
  * add quest to object of completed quests and store in localStorage

### end

* Score the adventure based on health and gold
* Display text explaining how the adventure went

## Slices

 ### index page
  * create `index.html`, `src/home/index.js` and `src/home/index.css` files
  * html
    * create a `user-signin` form
      * create a `name` text input
      * create `race` radio buttons
  * js
    * add a `submit` listener
    * on submit create a user object with name, race, hp, and gold
    * store user in localStorage
    * redirect to map.html

### add quests to map page
  * create `map.html`, `src/quests.js`, `src/map/map.js` and `src/map/map.css` files
  * html
    * create a `nav` element, which will store a list of quests
  * js
    * `src/quests.js`
      * export an array with quest names `['treasure', 'monsters']`
    * `src/map/map.js`
      * import `quests.js`
      * for each quest place create a link to the quest

### create quest page
  * create `quest.html`, `src/quest/quest.js`, `src/quest/quest.css`
  * html
    * add h2 title for quest title
  * js
    * `src/quests.js`
      * update quests array. a quest should be an object
        with id and title.
    * `src/quest/quest.js
      * import quests.js
      * get quest id from url search params
      * find quest in array of quests by id
      * add quest title to page

### add more quest info
  * html
    * add place for quest image
    * add place for quest audio
    * add place for quest description
    * add form for quest choices
  * js
    * `src/quests.js`
      * add image, audio, description and choices to quests
        * choices should be an array of objects
          * each object has an id, description, result, hp, and gold
          * the hp and gold properties represent how the users
             hp and gold will change when the choice is selected.
    * `src/quest/quest.js`
      * add quest image, audio, description, and choices to page.

### on quest submit
  * js
    * get selected choice from form (`FormData`)
    * find choice in `quest.choices`
    * get user from localStorage
      * `getItem`
    * update users hp and gold based on choice
    * save user back to localStorage
      * `setItem`
    * redirect back to map.html

### update map page base on new quests array
  * js
    * for each quest
      * get the quests id to create a link
      * get the quests title to create text for the link

### remove completed quest from map
  * js
    * `src/home/index.js
      * create an empty object (this will store completed
        quests)
      * store object in localStorage
    * `src/map/map.js`
      * get `completed` from localStorage
      * if quest exists in `completed` don't display quest link
    * `src/quest/quest.js`
      * js
        * on submit add quest to completed object
          * the key should the quest's id and the value should be true
          * get `completed` from localStorage
          * save `completed` to localStorage after adding quest

### go to end game
  * create `end.html`
  * html
    * Display "GAME OVER"
  * js
    * `src/map/map.js`
      * if user's hp is less than or equal to 0
        * go to end
      * if all quests completed (completed object has all quests)
        * go to end

### show stats at end
  * create `src/end/end.js`
  * html in `end.html`
    * create element to display results
  * js in `end.js`
    * construct a message based on users current hp and gold
    * add message to results element

## Stretch Goals

