# Experience day exercise

## Blitzstack project

You can find this challenge here:
https://stackblitz.com/edit/merkle-experience-day-vuejs

⚠️ Blitzstack works best in Chrome (images are broken in Firefox (CSP header))

## Setup

To start and work on the case please do one of the following:

### Setup on stackblitz

```
- fork the stackblitz project
- if you want to play save, connect it to a repository with your github account
```

### Setup on your own machine

```
- fork the stackblitz project
- download the project to your machine (in project pane there is a "cloud with arrow" button)
- unzip folder
- `npm install` as usual and start the project `npm run dev`
- if you want to play save, connect it to a repository with your github account
```

## Start working

- just make sure you will not loose any code
- look at the code and get familiar with it
- you have tailwind already set up for you, but you can also use pure CSS (just use the index.css file or `<style>` tags in the SFC)
- please stop/record the time you work on the assignment. It should be less than 2h. If you cannot finish within 2 hours, just stop anyway, we still have enough code to talk about. (just be honest to yourself and us and keep the times "real" ;) )
- Bring your solutions to the tech interview session. If we do it remote: You can share your screen in our meeting (MS Teams), or you can setup a online "editor" (we recommend blitzstack.com)

When you finish the assignment, we will set up a tech interview on site or remote, where we discuss the solutions and topics around the challenges. There is no (perfect) score for the assignment. We will use it mainly for a base of discussion.

It also should be a little fun to work with code. So do not worry, and have fun.

## The Story

Our client has a VERY simple website.
He loves the simpsons. And he wants to show some quotes of the simpson characters on his website.
Since he knows some HTML and CSS he already started the project. But then gave up.
You pick up from here.

## Your challenges

### 0.) Center the headline

As a little warm up:

- horizontally center the headline "Simpson Quotes" in the page.
- center the quote under the image
- output the name of the character as well (you choose any "design")

### 1.) Fetch quotes from api

The client used some dummy data in the `List.vue` file. Make a request to the Api and fetch 3 items and display them (do not worry about layout yet).

API is `https://thesimpsonsquoteapi.glitch.me/quotes`

### 2.) Responsive layout

The client requests a responsive layout:

- on mobile: all cards full width (keep some margins to the edges)
- on tablet: 2 cards in one row
- on desktop: 3 cards in one row

(hint: use reasonable sizes for the viewports; up to you; maybe a "container" will be good for very large screens)

### 3.) Buttons to load 5, 10, 15 quote

We only load 1 quote on the start.
The client requests 3 buttons on the bottom of the page.

- Text: "5 Quotes are good" if you click on it fetches 5 Quotes
- Text: "10 Quotes are better" if you click on it fetches 10 Quotes
- Text: "15 Quotes are the best" if you click on it fetches 15 Quotes

You are free to "design" the buttons as you like.
(hint: later we will discuss what you picked (e.g. `<button> vs <a>`))

### 4.) Make it sort

At the top of the file, you will find 2 "Buttons" for sorting. The component was already created, but the client couldn't get it to work.

- make the 2 buttons work, so that they sort by the Name of the character
- make use of ONE button component and use it twice
- when the sorting is active, the button should somehow be "highlighted" (you choose the style)

### 5.) No Code question / discussion

This challenge is not about code. You do not have to write any code. But read the bullet points and think about the questions and maybe write some short notes about it. We will discuss these topics in our session.

#### Challenges

- After we implemented the "load 5/10/15" buttons, we found out, that when the user clicked the buttons multiple times, the API was crashing under the load of too many requests. Prepare an idea (or multiple?) how to prevent the user from sending too many requests to the API. Bring your ideas in "words" / bullet points to the interview. (no code needed)
- After we deploy our nice website, we found out, that we have some accessibility issues. Can you find some issues about accessability and do you know how to address them? What can we do to make our site more accessible. (Please do not change your code at this point. We never had Accessibility as a requirement, so it's OK to have these issues)
- Think about the current state of the application. What did the client forget? What issues or ideas do you have as a developer, to make the site more stable and robust. We will discuss.


##### Improvements (Mannar)
1- I'd extract the fetching method to its own service/file and import it in the component (advantage: re-use it by another component). Also Vuex could be used here if there are lots of communicating between parent and children components.

2- I would extract the components style (btn, section, row) to their own stylesheet files ( modular structre)

3- for mouse-hater people, i'd double check the app using keyboard only (navigating through hitting tab only) and tweet the tabIndex

4- I would make a child and extract the article (the quote card) into its own child component (i.e ListItem) => cleaner List.vue

5- that's all i could think of. for now :)