## NightWatch-CircleCI-ORB-Sample
##### [NightWatch Documentation](http://nightwatchjs.org/)
![LAMBDATEST Logo](http://labs.lambdatest.com/images/fills-copy.svg)
----
This is sample repository for CircleCI ORBS.
----
### Environment Setup

1. Global Dependencies
    * Install [Node.js](https://nodejs.org/en/)
    * Or Install Node.js with [Homebrew](http://brew.sh/)
    ```
    $ brew install node
    ```
2. lambdatest Credentials
    * In the terminal export your lambdatest Credentials as environmental variables:
    ```
    $ export LT_USERNAME=<your lambdatest username>
    $ export LT_ACCESS_KEY=<your lambdatest access_key>
    ```
3. Project Dependencies
    * Install Node modules
    ```
    $ npm install
    ```

### Running Tests

* Tests in Parallel:

    ** Linux/Mac
    ```
    $ ./node_modules/.bin/nightwatch -e chrome,edge,firefox tests
    ```
   ** Windows
    ```
    $ node_modules\.bin\nightwatch -e chrome,edge,firefox tests
    ```

You will see the test result in the [lambdatest Dashboard](https://automation.lambdatest.com)

## Circle CI ORB Config.
---
```
version: 2.1

orbs:
    lambda-dev: lambdatest/lambda-tunnel@volatile

workflows:      
    basic_workflow:
        jobs:
          - lambdatest/with_tunnel:
              name: "Chrome test"
              tunnel_name: "chrome"
              steps:
                - run: 
                    command: |
                      npm install
                      node_modules/.bin/nightwatch -e chrome
          - lambdatest/with_tunnel:
              name: "Firefox test"
              tunnel_name: "firefox"
              steps:
                - run: 
                    command: |
                      npm install
                      node_modules/.bin/nightwatch -e firefox

```
----
## About LambdaTest

[LambdaTest](https://www.lambdatest.com/) is a cloud based selenium grid infrastructure that can help you run automated cross browser compatibility tests on 2000+ different browser and operating system environments. All test data generated during testing including Selenium command logs, screenshots generated in testing, video logs, selenium logs, network logs, console logs, and metadata logs can be extracted using [LambdaTest automation APIs](https://www.lambdatest.com/support/docs/api-doc/). This data can then be used for creating custom reports.

### Resources

##### [SeleniumHQ Documentation](http://www.seleniumhq.org/docs/)

