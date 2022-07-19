# Games with Words

## Overview
Games with Words is a project that was inspired by browser game grab-bag websites. All of the games that are currently supported and currently under construction will have something to do with words. This is the first full-stack project that I'm creating on my own, so there are lots of great opportunities to learn along the way!

## Planned Features

### Optional Login and Progress Tracking
Users will be able to log into the Games with Words site and keep track of their progress through the different levels of each game. I plan to leverage Auth0 for authentication and integrate it into my application. For privacy reasons, I want to avoid storing any information aside from a user-chosen username in the database for login and tracking.

### Multiple Games
I plan to implement a range of word games such as hangman, word search and crossword puzzles.

## Development Tech Stack
On the front-end, I am using VueJS as my front-end framework and Vite as my build tool. So far, I've absolutely loved how fast things update while I build the UI. To help with styling, I plan to use Bootstrap in conjunction with Vue. Additionally, I will be using Vitest as my testing suite on the front-end as this is the tool that's recommended in the Vue documentation.

For back-end logic, I will be building an API in Express to handle all of the game logic. The games will be mostly puzzle-style, so it wouldn't make sense to have the answers to the puzzles conveniently accessible in the Javascript itself. I will be using Mocha and Chai to write tests for the API logic.

## Deployment Tech Stack
The front-end of the application will be hosted using an AWS S3 bucket with static hosting enabled. The S3 bucket will be updated as part of my GitHub Actions pipeline that runs on each merge with the Main branch.

For the API, I debated between using API Gateway + Lambda or using AWS ECS to run the API on a container. Ultimately, I decided to go with ECS for this project because I worry about the potentially latency that may be felt by users from cold starts. I've read about some methods for keeping Lambda functions warm without incurring too much cost, so that may be something to explore in the future!
