# CircleCI-Practice


version: 2.1
orbs:
  node: circleci/node@1.1
jobs:
  build:
    docker:
      - image: circleci/node:10.4
    steps: 
      - checkout
      - run: echo "npm install"
      - run: npm run install
      - run: CI=true npm run build
  hi:
    docker:
      - image: circleci/node:10.4
      - run: 'Hi there'
  test:
    docker:
      - image: circleci/node:10.4
    steps: 
      - checkout 
      - run: echo "test executing"
workflows: 
  version: 2
  build_test_and_lint:
    jobs:
      - build
      - hi
      - test:
        requires: hi
      
 
     
