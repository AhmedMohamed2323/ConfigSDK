Steps

1) Create a Github Repo 

2) Create in VS Code 

├── .circleci
│   ├── setup.yml (config.yml)
├── └── generated (dynamic)
│       ├── generated.index.js (index.js)
│       ├── package.json
│       └── package-lock.json
├── src

Dynamic folder contains index.js, package-lock.json and package.json files

2) Install the config SDK
    Installation
    Using npm: $ npm i @circleci/circleci-config-sdk

3) Generate a CircleCI config using TypeScript/Javascript, properly typed for full IntelliSense support.

Take below Circleci Script () and create a index.js () * Note Script below isn't the standard. Subject to change due to your own personal build. End goal: myConfig.writeFile('config.yml'

const CircleCI = require('@circleci/circleci-config-sdk');
// Instantiate new Config
const myConfig = new CircleCI.Config();
// Create new Workflow
const myWorkflow = new CircleCI.Workflow('myWorkflow');
myConfig.addWorkflow(myWorkflow);

// Create an executor instance
// Executors are used directly in jobs
// and do not need to be added to the config separately
const nodeExecutor = new CircleCI.executors.DockerExecutor('cimg/node:lts');

// Create Job and add it to the config
const nodeTestJob = new CircleCI.Job('node-test', nodeExecutor);
myConfig.addJob(nodeTestJob);

// Add steps to job
nodeTestJob
  .addStep(new CircleCI.commands.Checkout())
  .addStep(
    new CircleCI.commands.Run({
      command: 'npm install',
      name: 'NPM Install',
    }),
  )
  .addStep(
    new CircleCI.commands.Run({
      command: 'npm run test',
      name: 'Run tests',
    }),
  );

// Add Jobs to Workflow
myWorkflow.addJob(nodeTestJob);

// The `stringify()` function on `CircleCI.Config` will return the CircleCI YAML equivalent.
const MyYamlConfig = myConfig.stringify();

// Save the config to a file in Node.js or the browser. Note, use in the browser requires user interaction.
myConfig.writeFile('config.yml');

MyYamlConfig: dynamicConfig.yml: Config.yml

version: 2.1
setup: false
jobs:
  node-test:
    docker:
      - image: cimg/node:lts
    resource_class: medium
    steps:
      - checkout: {}
      - run:
          command: npm install
          name: NPM Install
      - run:
          command: npm run test
          name: Run tests
workflows:
  myWorkflow:
    jobs:
      - node-test: {}

----------------------------------------------

generate-config: 
https://app.circleci.com/pipelines/github/AhmedMohamed2323/ConfigSDK/34/workflows/66dc674e-1a6b-4445-b1fa-0fbbfa5c48a6/jobs/39


Spin up environment
1s

Preparing environment variables
0s

Checkout code
0s

Checking for package.json
0s

Determine lockfile
0s

Restoring cache
0s

Installing NPM packages
0s

Saving cache
0s

Remove temporary links
0s

Generate config
0s

Continue Pipeline

-------------------------
echo-hello-world-test:

https://app.circleci.com/pipelines/github/AhmedMohamed2323/ConfigSDK/34/workflows/1b7df6d1-c80f-4b6b-857c-60937187b014/jobs/40


Spin up environment
1s

Preparing environment variables
0s

Checkout code
0s

echo test
