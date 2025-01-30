---
layout: assignment
title: "Individual Project 2"
permalink: /assignments/ip2
parent: Assignments
nav_order: 2
due_date: "Wednesday February 19, 2025 12:00pm EST (Noon)"
submission_notes: Submit through Github Classroom (Commit your work in main branch)
---

Welcome back to the Stack Overflow team! In this second deliverable, you will be implementing new and exciting features to enhance the frontend interface and bring the web application to life. This assignment builds on the foundation you laid in the first project and will deepen your skills in frontend development with TypeScript and React.

## Objectives of this assignment

The objectives of this assignment are to:

- Investigate and understand a large, existing codebase
- Write new TypeScript code that uses asynchronous operations
- Write test cases that utilize mocks and spies
- Write React components and hooks that make use of state

## Getting started with this assignment

Start by accepting our [invitation](https://classroom.github.com/a/avzeZ5De). It will create a Github repository for you which will include the starter code for this assignment. Run npm install within `./client` and `./server` to fetch the dependencies. You should not install any additional dependencies: **‘package.json’ must be unchanged**.

{ : .note }
Refer to [IP1](https://neu-se.github.io/CS4530-Spring-2025/assignments/ip1) for instructions related to setting up MongoDB, setting environment variables, and running the client and server.

{: .note }
**System-level dependencies:** The libraries used for React require some native binaries to be installed -- code written and compiled for your computer (not JavaScript). If you run into issues with `npm install` not succeeding, please try installing the following libraries using either [Homebrew (if on Mac)](https://brew.sh), apt-get, or your favorite other package manager: `pixman`, `cairo`, `pkgconfig` and `pango`. For example, on a Mac, after installing Homebrew, run `brew install pixman cairo pkgconfig pango`. **You should not continue with the installation until this succeeds.** On Windows: Students have reported seeing the failure `error /bin/bash: node: command not found` upon `npm install` in the `client` directory. If you encounter this error, please try to delete the `node_modules` directory and re-run `npm install` in the `client` directory from a bash shell instead of a windows command prompt.

These are some convenience scripts that you can use while working on the assignment:

1. `npm start` / `npm run start` (client + server) - This can be used to start the client or server in the respective directory the command is run. Both the client and server will reload every time a file is saved, reflecting any changes live.
2. `npm run debug-test` (server)- This runs the test command without checking for memory leaks. Often, the Jest memory leak error is introduced by failing tests, so resolving any errors should be the first step in debugging the memory leak. `npm test` / `npm run test` will be used for grading, however, so ensure your GitHub Actions workflow is passing.

## Implementation Tasks

This deliverable has 3 parts; each part will be graded by its own rubric provided in the "Grading" section. You're recommended to complete this assignment one task at a time, in the order provided. For this assignment, follow test-driven development (TDD). Read the tests to understand how the functions are expected to behave and use that understanding to inform your implementation. Do **not** change the provided tests to match your implmentation.

### Task 1: User-Related Pages

In IP1, we defined several API routes and database operations to support users on the forum. In particular, we added the following features:

1. Sign up
2. Get an account by the username
3. Log in
4. Reset their password
5. Delete their account

In this task, we'll build on this to allow users to interact with it in the frontend, as well as add some additional functionality to bring our forum to life.

#### Steps to Achieve This

1. **Implement `useAuth` custom hook logic**

   This custom hook is responsible for all authentication tasks (login and signup), found in `client/src/hooks/useAuth.ts`. Follow the inline comments to complete the functions. We'll make use of the logic implemented here in the respective authentication components as required. Helper functions for making API requests can be found in `client/src/services`.

2. **Complete the `Login` component form**

   This form component in `client/src/components/auth/login/index.tsx` takes the username and password inputs and handles the login flow on submission. The input fields are removed: use the logic implemented from the `useAuth` hook to appropriately complete the form. Follow the inline comments for guidance.

   Make sure that the password visibility is correctly toggled: when `showPassword` is false, the password should appear as dots, and when true, the user should be able to see the text entered.

3. **Complete the `Signup` component form**

   This form component in `client/src/components/auth/signup/index.tsx` takes the username, password, and password confirmation inputs and handles the signup flow on submission. The input fields are removed: use the logic implemented from the `useAuth` hook to appropriately complete the form. Follow the inline comments for guidance.

   Similar to the `Login` component, make sure that the password visibility is correctly toggled for both the password and confirm password fields.

4. **Add a `biography` field for users**

   Update the `userSchema` in `server/models/schema/user.schema.ts` to include an optional biography field that has a default value of an empty string. The TypeScript types have already been updated for you to include the `biography` field.

5. **Implement the `updateBiography` endpoint**

   In `server/controllers/user.controller.ts`, implement the `PATCH` `updateBiography` API route to allow a user to update their biography. Think about how you might implement this with the services implemeneted in IP1.

   You'll also need to define the request interface in `server/types/user.d.ts` to have the required properties.

6. **Complete the `ProfileSettings` component and `useProfileSettings` custom hook**

   What forum would be complete without a profile page? This component serves several purposes. For users viewing their own profile, we'll allow them to access profile settings, such as editing their biography, resetting their password, and deleting their account (why would you ever want to leave HuskyFlow?). For users browsing another profile, they should only be able to view the general information and not perform account edits(!).

   Follow the inline comments for guidance on how to complete this. The component can be found in `client/src/components/profileSettings/index.tsx` and the hook is in `client/src/hooks/useProfileSettings.ts`

7. **Implement the `getUsersList` service and `getUsers` endpoint**

   In `server/services/user.service.ts`, implement the `getUsersList` service, which queries the database for all the users, and removes the password from each of the users (our "security feature" from IP1).

   In `server/controllers/user.controller.ts`, implement the `GET` `getUsers` API route to retrieve a list of all users from the database. Ensure appropriate error handling.

8. **Complete the `Users` page**

   This page makes use of several sub-components and custom hooks to display a list of all users, filtered by the current search term entered into the search bar. The search filters out any usernames that do not contain the substring entered into the search bar. This should update after every character entered into the field.

   Refer to the following files:

   - `client/src/components/main/usersListPage/index.tsx`
   - `client/src/components/main/usersListPage/header/index.tsx`
   - `client/src/components/main/usersListPage/userCard/index.tsx`
   - `client/src/hooks/useUsersListPage.ts`
   - `client/src/hooks/useUserSearch.ts`

9. **Test all added server functions**

   We’ve provided initial tests to provide some information on the expected behavior of the routes and functions. Using the requirement descriptions above, write additional tests for all the added functions and routes, covering different branches, edge cases, etc. to verify the correctness of your code.

   In addition to automated tests, you should also manually test your route using Postman and MongoDB Compass to ensure that any database queries are correct since we use database mocks while testing with Jest.

   While we do not require automated frontend tests, you should extensively test your implementation manually, exploring edge cases in the browser.

#### Grading (56 points)

- `useAuth` hook = 8 points
- `Login` component = 4 points
- `Signup` component = 5 points
- Add `biography` to user schema = 1 point
- `updateBiography` endpoint = 3 points
- `useProfileSettings` hook = 10 points
- `ProfileSettings` component = 5 points
- `getUsersList` service = 2 points
- `getUsers` endpoint = 2 points
- `Users` page = 10 points
  - `UsersListHeader` = 1
  - `UsersListPage` = 2
  - `useUserSearch` = 2
  - `useUsersListPage` = 5
- Testing = 6 points

### Task 2: Games

Let's liven up the forum by adding some games! In this task, we'll be implementing some components to allow users to play games of Nim against each other.

There are many variations of [Nim](https://en.wikipedia.org/wiki/Nim), but for this assignment we'll be using the following rules:

- The pile of objects starts with 21 objects
- Players take turns removing between 1 and 3 (inclusive) objects from the pile
- A player cannot remove more objects than remaining in the pile
- The player to remove the final objects from the pile loses the game

The backend is implemented for you, with the main focus on working with React and sockets for this task. We encourage you to go through the server code and tests to better understand the API routes and game mechanisms.

#### Steps to Achieve This

1. **Complete the `useAllGamesPage` custom hook**

   In `client/src/hooks/useAllGamesPage.ts`, follow the inline comments to complete the logic. We'll make use of this within the `AllGamesPage` component later.

2. **Complete the `GameCard` component**

   In `client/src/components/main/games/allGamesPage/gameCard/index.tsx`, we've defined a component to display a single game within the list of games on the "Games" page (to be completed in the next step). Complete the conditionally rendered join button, such that the user is only able to join a game that is waiting to start.

3. **Complete the `AllGamesPage` component**

   In `client/src/components/main/games/allGamesPage/index.tsx`, we've defined a component to represent the "home" page for all games. It displays a list of all the games, allowing the user to view and join a game. Joining a game will navigate the user to a separate game-specific page, which we'll implement in the following steps.

4. **Complete the `useGamePage` custom hook**

   In `client/src/hooks/useGamePage.ts`, follow the inline comments to complete the logic. We'll make use of this within the `GamePage` component in the next step.

5. **Complete the `GamePage` component**

   In `client/src/components/main/games/gamePage/index.tsx`, we've defined a component to display the game-specific state. It conditionally renders a sub-component for displaying the game state, based on the type of game. Follow the inline comments to complete this component.

6. **Complete the `useNimGamePage` custom hook**

   In `client/src/hooks/useNimGamePage.ts`, follow the inline comments to complete the logic. We'll make use of this within the `NimGamePage` component in the next step.

7. **Complete the `NimGamePage` component**

   In `client/src/components/main/games/nimGamePage/index.tsx`, we've defined a component to display the Nim game state. It displays the rules of the game, the current game state information, and has input to make a move. Follow the inline comments to complete the component.

#### Grading (43 points)

- `useAllGamesPage` hook = 6 points
- `GameCard` component = 3 points
- `AllGamesPage` component = 5 points
- `useGamePage` hook = 12 points
- `GamePage` component = 5 points
- `useNimGamePage` hook = 5 points
- `NimGamePage` component = 7 points

### Task 3: Direct Messages

In this task, you will implement a chat system that allows users to create chats, add messages, retrieve chats, and add participants. You will be working on the backend and database layers to implement this functionality, and complete some frontend components to allow the user to interact with it.

#### Steps to Achieve This - Server

1. **Define the `Chat` schema**

   - In `server/models/schema/chat.schema.ts`, define the Mongoose schema for the `Chat` collection.
   - The schema should include:
     - `participants`: An array of strings representing the usernames of users in the chat.
     - `messages`: An array of ObjectIds referencing the `Message` collection.
     - Automatic timestamps (`createdAt`, `updatedAt`) for tracking when chats are created or updated.

2. **Define the `Chat` model**

   - In `server/models/chat.model.ts`, define the mongoose model to be able to perform database operations.

3. **Define relevant TypeScript types**

   - In `server/types/chat.d.ts`, define the relevant types as marked by TODO: Task 3. Make sure to avoid repeated definitions of fields between the interfaces.

4. **Implement validation helpers**

   - In `server/controllers/chat.controller.ts`, create helper functions to validate request payloads:

     - `isCreateChatRequestValid`: Validates that the request body contains valid `participants` and `messages`.
     - `isAddMessageRequestValid`: Validates that the request body contains valid `msg`, `msgFrom`, and `msgDateTime`.
     - `isAddParticipantRequestValid`: Validates that the request body contains a valid `userId`.

   - Each helper function should return `true` if the request is valid and `false` otherwise.

5. **Implement service functions**

   - In `server/services/chat.service.ts`, implement the following service functions:

     - `saveChat`: Creates and saves a new chat document in the database. Ensure messages are dynamically created and referenced in the chat.
     - `createMessage`: Creates and saves a new message document in the database.
     - `addMessageToChat`: Adds a message ID to an existing chat and updates it in the database.
     - `getChat`: Retrieves a chat document by its ID from the database.
     - `addParticipantToChat`: Adds a new participant to an existing chat by updating the `participants` array.
     - `getChatsByParticipants`: Returns all chats where the participants list includes all of the participants provided as an argument to the function.

   - Ensure all service functions handle errors gracefully and return appropriate error responses.

6. **Implement join/leave socket room events**

   Since these are direct messages, we want to make sure that only the intended participants receive message updates. Socket rooms allow us to send events specifically to a list of subscribed participants, keeping messages private.

   For each chat, create a room using the `chatID` provided as part of the `joinChat` socket event emitted by the client. Chat-specific updates, such as a new message, should only be emitted to this room.

   Also, implement the `leaveChat` socket listener, so that the client can unsubscribe from the socket room and stop receiving updates. Only leave the socket room if the provided chatID is defined.

7. **Implement controller functions**

   - In `server/controllers/chat.controller.ts`, implement the following routes:

     - `createChatRoute`: Handles `POST` requests to create a new chat using `saveChat`. Enrich the result using the `populateDocument` utility. A `chatUpdate` socket event is emitted to notify the client.
     - `addMessageToChatRoute`: Handles `POST` requests to add a message to an existing chat using `createMessage` and `addMessageToChat`. A `chatUpdate` socket event is emitted to notify the client that a new message was added to the chat. This socket event should **only** be emitted to users currently in the specific chat room.
     - `getChatRoute`: Handles `GET` requests to retrieve a chat by ID using `getChat`. Enrich the result using the `populateDocument` helper function.
     - `addParticipantToChatRoute`: Handles `POST` requests to add a participant to an existing chat using `addParticipantToChat`.
     - `getChatsByUserRoute`: Handles `GET` requests to retrieve all chats that contain the username that is provided as part of the route parameters. Populate all of the chat documents before returning a response. Throw an error if the population fails for _any_ of the chats.

   - Refer to the tests provided for guidance on how to define the router endpoints.

   - Use the validation helpers (`isCreateChatRequestValid`, `isAddMessageRequestValid`, `isAddParticipantRequestValid`) to validate incoming requests before processing them.

8. **Test functionality**

   - In `server/tests/services/chat.service.spec.ts`, write unit tests for:

     - `saveChat`
     - `createMessage`
     - `addMessageToChat`
     - `getChat`
     - `addParticipantToChat`
     - `getChatsByParticipants`

   - Ensure the tests cover all possible scenarios, including success and failure cases.

   - In `server/tests/controllers/chat.controller.spec.ts`, write tests for:

     - `createChatRoute`
     - `addMessageToChatRoute`
     - `getChatRoute`
     - `addParticipantToChatRoute`
     - `getChatsByUserRoute`
     - Ensure that all routes are properly tested for validation, success, and error responses.

   - Manually test the chat functionality using tools like Postman or a frontend.
   - Ensure that chats, messages, and participants are being created, retrieved, and updated as expected. A key consideration here is that the list of messages for a chat **should not be** a list of ObjectIDs when returned from the endpoint - the complete message object should be returned.

#### Steps to Achieve This - Client

1. **Complete the `ChatsListCard` component**

   Similar to the game card component, the `ChatsListCard` component in `client/src/components/main/directMessage/chatsListCard/index.tsx` is reponsible for displaying general information about the chat participants. Follow the inline comments to complete this.

2. **Complete the `useDirectMessage` custom hook**

   In `client/src/hooks/useDirectMessage.ts`, the custom hook handles the logic for the `DirectMessage` component. Follow the inline comments to complete this.

3. **Complete the `DirectMessage` component**

   This component, defined in `client/src/components/main/directMessage/index.tsx`, displays all the available chats for a user, allows them to create new chats, view specific chats, and send new messages. We've removed some pieces of the component, follow the inline comments to complete this.

4. **Manual Testing**

   Though automated tests are not required for frontend functionality, we strongly suggest exntesively testing each of the components extensively. Explore edge cases in your browser to identify potential bugs in the functionality. Remember - if the socket code is correctly set up, each update should instantly show up across 2 tabs open in parallel, without needing to navigate away from the page. Try chatting between 2 different users to test your implementation.

#### Grading (81 points)

- Define Schema, Model, and Chat Types = 4 points
  - Chat schema and model = 2
  - TypeScript types in `chat.d.ts` = 2
- Implement `chat.service.ts` Functions = 9 points
  - `saveChat` = 2
  - `createMessage` = 2
  - `addMessageToChat` = 1
  - `addParticipantToChat` = 2
  - `getChat` = 1
  - `getChatsByParticipants` = 1
- Implement `chat.controller.ts` Endpoints = 18 points
  - `isCreateChatRequestValid` = 2
  - `isAddMessageRequestValid` = 2
  - `isAddParticipantRequestValid` = 1
  - `createChatRoute` = 3
  - `addMessageToChatRoute` = 4
  - `addParticipantToChatRoute` = 2
  - `getChatRoute` = 2
  - `getChatByParticipants` = 2
- Join chat event = 2 points
- Leave chat event = 2 points
- Testing = 20 points
  - Testing `chat.service.ts` = 10
  - Testing `chat.controller.ts` = 10
- `ChatsListCard` component = 2 points
- `useDirectMessage` hook = 15 points
- `DirectMessage` component = 9 points

## Submission Instructions & Grading

You will submit your assignment using GitHub Classroom. **All commits must be visible on the main branch on GitHub classroom to receive credit.**

This submission will be scored out of 200 points, 180 of which will be awarded for implementation of tasks and accompanying tests, and the remaining 20 for following style guidelines.

Your code will automatically be evaluated for linter errors and warnings.

- Each lint error or warning will result in a deduction of -2 points (up to a maximum of 30 points).
- This will not affect the 20 style points.
- Line endings will not be counted as errors.

The starter code comes with some lint problems, You are expected you to fix these linter problems, many of them will be fixed as you implement the tasks.

**The use of `eslint-disable` statements is NOT allowed. Each instance outside what is provided in the starter code will have points deducted.**

You can run the following command within the client or server to fix some common lint errors

```
npm run lint:fix
```

#### Testing

You will be provided with starter code that includes a set of tests. Your task is to ensure that all existing tests pass and to create additional tests to cover any new functionality or edge cases in the server. You do not need to write automated tests for the frontend, but are encouraged to extensively manually test your implementation.

### Manual Grading

Your code will be manually evaluated for conformance to our [course style guide](https://neu-se.github.io/CS4530-Spring-2025/policies/style/). **Do not wait to run the linter until the last minute**. To check for linter errors, run the command `npm run lint` from the terminal. The handout contains the same ESlint configuration that is used by our grading script.

This manual evaluation will account for 10% of your total grade on this assignment. We will manually evaluate your code for style on the following rubric:

To receive all 10 points:

- All new names (e.g. for local variables, methods, and properties) follow the naming conventions defined in our style guide
- There are no unused local variables
- All public properties and methods (other than getters, setters, and constructors) are documented with JSDoc-style comments that describe what the property/method does, as defined in our style guide
- The code and tests that you write generally follows the design principles discussed in week one. In particular, your design does not have duplicated code that could have been refactored into a shared method.
- No duplicate code is allowed.

We will review your code and note each violation of this rubric. We will deduct 2 points for each violation, up to a maximum of deducting all 10 style points.

#### GitHub Actions for Test and Lint Output

Once your submission is pushed to your main branch, GitHub will automatically run linting and the tests in `server/tests` for your submission. Check the Actions tab on GitHub classroom to see the output of the run. This output will be used for grading, so ensure there are no errors in the Actions run.

![image]({{site.baseurl}}{% link /Assignments/ip1/ActionsTab.png %})

#### Debugging

If you need help troubleshooting a problem, be sure to follow all the steps outlined in the course's [debugging policy]({{ site.baseurl }}{% link debugging.md %}). This will ensure you have exhausted all initial debugging strategies before reaching out for assistance from the TAs.

### Academic Integrity

Please refer to the [course policy page](https://neu-se.github.io/CS4530-Spring-2025/policies/#academic-integrity) for more details.

**For this assignment, the use of co-pilot or other generative AI technologies such as ChatGPT is not allowed.**
