## Improvement Proposals

### Code quality and readability

- The project has eslint, but current linting rules are insufficient, and as I can see they aren't properly forced. I would propose to fix it first.
- The project is mainly relying on the "@hubspot/api-client" lib, which is typed using Typescript. I would propose adding Typescript to the project, setting proper eslint rules for it, renaming files from "*.js" to "*.ts" and eventually rewriting everything to be typed.

### Project architecture

- The project is very chaotic at the moment. I would propose to firstly create a basic structure for the project directory-wise (src -> api, utils, jobs). And then I would propose to logically divide big files and methods into smaller ones, it would really increase code reusability.

### Code performance

- Worker file is currently running in the same thread with the server. And then there're 3 jobs in the worker file running in sequence, when they in fact can be run in parallel. I would propose to firstly make the worker file run in a different worker thread (https://nodejs.org/api/worker_threads.html). And then we can also divide the worker file into reusable common parts, and split the jobs to different files to make it possible to run them all in different threads, basically making them run in parallel.
