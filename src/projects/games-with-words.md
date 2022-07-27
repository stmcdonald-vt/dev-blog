# Games with Words

## Overview
Games with Words is a project that was inspired by browser game grab-bag websites. All of the games that are currently supported and currently under construction will have something to do with words. This is the first full-stack project that I'm creating on my own, so there are lots of great opportunities to learn along the way!

## Development Tech Stack
On the front-end, I am using VueJS as my front-end framework and Vite as my build tool. So far, I've absolutely loved how fast things update while I build the UI. To help with styling, I plan to use Bootstrap in conjunction with Vue.

For back-end logic, I will be building an API in Express to handle all of the game logic. The games will be mostly puzzle-style, so it wouldn't make sense to have the answers to the puzzles conveniently accessible in the Javascript itself. I will be using Mocha and Chai to write tests for the API logic.

## Deployment Tech Stack
The front-end of the application will be hosted using an AWS S3 bucket with static hosting enabled. The S3 bucket will be updated as part of my GitHub Actions pipeline that runs on each merge with the Main branch.

For the API, I debated between using API Gateway + Lambda or using Fargate to run the API on a container. Ultimately, I decided to go with Lambda for the project as the cost is considerably less and the only downside is a hit in latency from cold-starts. In my testing so far the latency is only slightly noticeable and since the games won't really be "real time", their sensitivity to latency should be low overall. Currently I have my Express API running on a single Lambda function and API Gateway proxying all routes through it. While this seems to work fine now, I don't think this will scale well into the future. Once I start to implement a few more services, I plan to split the API into microservices and dedicate one Lambda function to each microservice.

## Planned Features

### Strong Accessibility
To get the application into a barebones proof-of-concept state, not enough thought went into accessibility quite yet. Before building out much more of the application, accessibility should be revisited for the current content and be a priority moving forward. Remember, it's always easier to build accessibility from the start than to patch it in later!

### Automated UI Testing
I need to get automated testing configured for the UI of the project ASAP. Currently, I'm considering using [Vitest](https://vitest.dev/guide/filtering.html) as I'm currently using Vite and it is recommended in the Vue documentation. 

### Optional Login and Progress Tracking
Users will be able to log into the Games with Words site and keep track of their progress through the different levels of each game. I plan to leverage Auth0 for authentication and integrate it into my application. For privacy reasons, I want to avoid storing any information aside from a user-chosen username in the database for login and tracking. This will give me the opportunity to leverage DynamoDB and get some hands-on experience with it.

### Multiple Games
I plan to implement a range of word games such as hangman, word search and crossword puzzles.