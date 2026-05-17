# Run NightWatch with CircleCI ORB on TestMu AI (Formerly LambdaTest)

<p align="center">
  <a href="https://www.testmuai.com/"><img src="https://img.shields.io/badge/MADE%20BY%20TestMu%20AI-000000.svg?style=for-the-badge&labelColor=000" alt="Made by TestMu AI"></a>
  <a href="https://circleci.com/developer/orbs/orb/lambdatest/lambda-tunnel"><img src="https://img.shields.io/badge/CircleCI-ORB-343434.svg?style=for-the-badge&labelColor=000" alt="CircleCI ORB"></a>
  <a href="https://community.testmuai.com/"><img src="https://img.shields.io/badge/Join%20the%20community-blueviolet.svg?style=for-the-badge&labelColor=000000" alt="Community"></a>
</p>

## Getting Started

[TestMu AI](https://www.testmuai.com/) (Formerly LambdaTest) is the world's first full-stack AI Agentic Quality Engineering platform that empowers teams to test intelligently, smarter, and ship faster. Built for scale, it offers a full-stack testing cloud with 10K+ real devices and 3,000+ browsers. With AI-native test management, MCP servers, and agent-based automation, TestMu AI supports Selenium, Appium, Playwright, and all major frameworks. 

With TestMu AI (Formerly LambdaTest), you can run NightWatch tests via CircleCI ORBs across real browsers and operating systems. This sample shows how to configure NightWatch with the TestMu AI (Formerly LambdaTest) CircleCI ORB to run on the TestMu AI cloud.

- [Sign up on TestMu AI](https://www.testmuai.com/register/) (Formerly LambdaTest).
- Follow the [TestMu AI Documentation](https://www.testmuai.com/support/docs/) for the full setup walkthrough.

### Prerequisites

- [Node.js](https://nodejs.org/en/) installed on your system.
- A TestMu AI (Formerly LambdaTest) account. [Sign up here](https://www.testmuai.com/register/).
- Your TestMu AI Username and Access Key from your [profile page](https://accounts.lambdatest.com/detail/profile).
- A CircleCI account with the TestMu AI (Formerly LambdaTest) ORB enabled.

### Setup

1. Clone this repository:
    ```bash
    git clone https://github.com/LambdaTest/Lambdatest-circleci-orb
    cd Lambdatest-circleci-orb
    ```

2. Export your TestMu AI credentials as environment variables:
    ```bash
    export LT_USERNAME=<your lambdatest username>
    export LT_ACCESS_KEY=<your lambdatest access_key>
    ```

3. Install Node modules:
    ```bash
    npm install
    ```

### Run tests

#### Run tests locally

Run tests in parallel:

- Linux/Mac:
    ```bash
    ./node_modules/.bin/nightwatch -e chrome,edge,firefox tests
    ```
- Windows:
    ```
    node_modules\.bin\nightwatch -e chrome,edge,firefox tests
    ```

View results in the [TestMu AI Automation Dashboard](https://automation.lambdatest.com).

#### Run tests via CircleCI ORB

Configure your `.circleci/config.yml` to use the TestMu AI (Formerly LambdaTest) ORB:

```yaml
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

### Local testing with TestMu AI Tunnel

To test locally hosted apps, set up the TestMu AI tunnel. OS-specific guides:

- [Local Testing on Windows](https://www.testmuai.com/support/docs/local-testing-for-windows/)
- [Local Testing on macOS](https://www.testmuai.com/support/docs/local-testing-for-macos/)
- [Local Testing on Linux](https://www.testmuai.com/support/docs/local-testing-for-linux/)

The CircleCI ORB (`lambdatest/lambda-tunnel`) automatically manages tunnel setup and teardown for each job using the `lambdatest/with_tunnel` executor. Set a unique `tunnel_name` per job to identify each tunnel session.

## Contributions

Contributions are welcome. Open an issue to discuss your idea before submitting a pull request. When reporting bugs, include your Node.js version, OS, and Angular CLI version.

## TestMu AI (Formerly LambdaTest) Community

Connect with testers and developers in the [TestMu AI Community](https://community.testmuai.com/). Ask questions, share what you are building, and discuss best practices in test automation and DevOps.
  
## TestMu AI (Formerly LambdaTest) Certifications

Earn free [TestMu AI Certifications](https://www.testmuai.com/certifications/) for testers, developers, and QA engineers. Validate your skills in Selenium, Cypress, Playwright, Appium, Espresso and more. Industry-recognized, shareable on LinkedIn, and built by practitioners, not marketers.

## Learning Resources by TestMu AI (Formerly LambdaTest)

Learn modern testing through tutorials, guides, videos, and weekly updates:

* [TestMu AI Blog](https://www.testmuai.com/blog/)
* [TestMu AI Learning Hub](https://www.testmuai.com/learning-hub/)
* [TestMu AI on YouTube](https://www.youtube.com/@TestMuAI)
* [TestMu AI Newsletter](https://www.testmuai.com/newsletter/)
  
## LambdaTest is Now TestMu AI

On **January 12, 2026**, [LambdaTest evolved to TestMu AI](https://www.testmuai.com/lambdatest-is-now-testmuai/), the world's first fully autonomous **Agentic AI Quality Engineering Platform**.

Same team. Same infrastructure. Same customer accounts. All existing LambdaTest logins, scripts, capabilities, and integrations continue to work without change.

ð Find the new home for [LambdaTest](https://www.testmuai.com).

### How LambdaTest Evolved into TestMu AI

In 2017, we launched LambdaTest with a simple mission: make testing fast, reliable, and accessible. As LambdaTest grew, we expanded into Test Intelligence, Visual Regression Testing, Accessibility Testing, API Testing, and Performance Testing, covering the full depth of the testing lifecycle.

As software development entered the AI era, testing had to evolve, too. We rebuilt the architecture to be AI-native from the ground up, with autonomous agents that **plan, author, execute, analyze, and optimize tests** while keeping humans in the loop. The platform integrates with your repos, CI, IDEs, and terminals, continuously learning from every code change and development signal.

That evolution earned a new name: **TestMu AI**, built for an AI-first future of quality engineering. TestMu is not a new name for us. It is the name of our annual community conference, which has brought together 100,000+ quality engineers to discuss how AI would reshape testing, long before that became an industry norm. 

What started as a high-performance cloud testing platform has transformed into an AI-native, multi-agent system powering a connected, end-to-end quality layer. That evolution defined a new identity: LambdaTest evolved into TestMu AI, built for an AI-first future of quality engineering.

## Support

Got a question? Email [support@testmuai.com](mailto:support@testmuai.com) or chat with us 24x7 from our chat portal.
