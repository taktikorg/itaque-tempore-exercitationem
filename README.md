<span align="center">

![logo](./assets/logo-icon-small.svg)

# PactumJS

![Build](https://github.com/taktikorg/itaque-tempore-exercitationem/workflows/Build/badge.svg?branch=master)
![Coverage](https://img.shields.io/codeclimate/coverage/ASaiAnudeep/@taktikorg/itaque-tempore-exercitationem)
![Downloads](https://img.shields.io/npm/dt/@taktikorg/itaque-tempore-exercitationem)
![Size](https://img.shields.io/bundlephobia/minzip/@taktikorg/itaque-tempore-exercitationem)
![Platform](https://img.shields.io/node/v/@taktikorg/itaque-tempore-exercitationem)

[![Stars](https://img.shields.io/github/stars/@taktikorg/itaque-tempore-exercitationemjs/@taktikorg/itaque-tempore-exercitationem?style=social)](https://github.com/taktikorg/itaque-tempore-exercitationem/stargazers)
[![Twitter](https://img.shields.io/twitter/follow/@taktikorg/itaque-tempore-exercitationemjs?label=Follow&style=social)](https://twitter.com/@taktikorg/itaque-tempore-exercitationemjs)

#### REST API Testing Tool for all levels in a Test Pyramid

</span>

<br />
<p align="center"><a href="https://@taktikorg/itaque-tempore-exercitationemjs.github.io"><img src="https://raw.githubusercontent.com/@taktikorg/itaque-tempore-exercitationemjs/@taktikorg/itaque-tempore-exercitationem/master/assets/demo.gif" alt="PactumJS Demo"/></a>
</p>
<br />

<table>
<tr>
<td>

**PactumJS** is a REST API Testing Tool used to automate e2e, integration, contract & component (*or service level*) tests.

- ⚡ Swift
- 🎈 Lightweight
- 🚀 Simple & Powerful
- 🛠️ Compelling Mock Server
- 💎 Elegant Data Management
- 🔧 Extendable & Customizable
- 📚 Clear & Comprehensive Testing Style
- 🔗 Component, Contract & E2E testing of APIs

</td>
</tr>
</table>

![----------](https://raw.githubusercontent.com/@taktikorg/itaque-tempore-exercitationemjs/@taktikorg/itaque-tempore-exercitationem/master/assets/rainbow.png)

## Documentation

This readme offers an basic introduction to the library. Head over to the full documentation at https://@taktikorg/itaque-tempore-exercitationemjs.github.io

- [API Testing](https://@taktikorg/itaque-tempore-exercitationemjs.github.io/guides/api-testing)
- [Integration Testing](https://@taktikorg/itaque-tempore-exercitationemjs.github.io/guides/integration-testing)
- [Component Testing](https://@taktikorg/itaque-tempore-exercitationemjs.github.io/guides/component-testing)
- [Contract Testing](https://@taktikorg/itaque-tempore-exercitationemjs.github.io/guides/contract-testing)
- [E2E Testing](https://@taktikorg/itaque-tempore-exercitationemjs.github.io/guides/e2e-testing)
- [Mock Server](https://@taktikorg/itaque-tempore-exercitationemjs.github.io/guides/mock-server)

## Need Help

We use Github [Discussions](https://github.com/taktikorg/itaque-tempore-exercitationem/discussions) to receive feedback, discuss ideas & answer questions.

## Installation

```shell
# install @taktikorg/itaque-tempore-exercitationem as a dev dependency
npm install --save-dev @taktikorg/itaque-tempore-exercitationem

# install a test runner to run @taktikorg/itaque-tempore-exercitationem tests
# mocha / jest / cucumber
npm install --save-dev mocha
```

or you can simply use

```bash
npx @taktikorg/itaque-tempore-exercitationem-init
```

![----------](https://raw.githubusercontent.com/@taktikorg/itaque-tempore-exercitationemjs/@taktikorg/itaque-tempore-exercitationem/master/assets/rainbow.png)

# Usage

**@taktikorg/itaque-tempore-exercitationem** can be used for all levels of testing in a test pyramid. It can also act as an standalone mock server to generate contracts for contract testing.

## API Testing

Tests in **@taktikorg/itaque-tempore-exercitationem** are clear and comprehensive. It uses numerous descriptive methods to build your requests and expectations. 

### Simple Test Cases

#### Using Mocha

Running simple api test expectations.

```js
const { spec } = require('@taktikorg/itaque-tempore-exercitationem');

it('should be a teapot', async () => {
  await spec()
    .get('http://httpbin.org/status/418')
    .expectStatus(418);
});

it('should save a new user', async () => {
  await spec()
    .post('https://jsonplaceholder.typicode.com/users')
    .withHeaders('Authorization', 'Basic xxxx')
    .withJson({
      name: 'bolt',
      email: 'bolt@swift.run'
    })
    .expectStatus(200);
});
```

```shell
# mocha is a test framework to execute test cases
mocha /path/to/test
```

#### Using Cucumber

See [@taktikorg/itaque-tempore-exercitationem-cucumber-boilerplate](https://github.com/taktikorg/itaque-tempore-exercitationem-cucumber-boilerplate) for more details on @taktikorg/itaque-tempore-exercitationem & cucumber integration.

```gherkin
Scenario: Check Tea Pot
  Given I make a GET request to "http://httpbin.org/status/418"
  When I receive a response
  Then response should have a status 418
```

```js
// steps.js
const @taktikorg/itaque-tempore-exercitationem = require('@taktikorg/itaque-tempore-exercitationem');
const { Given, When, Then, Before } = require('@cucumber/cucumber');

let spec = @taktikorg/itaque-tempore-exercitationem.spec();

Before(() => { spec = @taktikorg/itaque-tempore-exercitationem.spec(); });

Given('I make a GET request to {string}', function (url) {
  spec.get(url);
});

When('I receive a response', async function () {
  await spec.toss();
});

Then('response should have a status {int}', async function (code) {
  spec.response().should.have.status(code);
});
```

## Mock Server

**@taktikorg/itaque-tempore-exercitationem** can act as a standalone *mock server* that allows us to mock any server via HTTP or HTTPS, such as a REST endpoint. Simply it is a simulator for HTTP-based APIs.

Running **@taktikorg/itaque-tempore-exercitationem** as a standalone *mock server*.

```js
const { mock } = require('@taktikorg/itaque-tempore-exercitationem');

mock.addInteraction({
  request: {
    method: 'GET',
    path: '/api/projects'
  },
  response: {
    status: 200,
    body: [
      {
        id: 'project-id',
        name: 'project-name'
      }
    ]
  }
});

mock.start(3000);
```

![----------](https://raw.githubusercontent.com/@taktikorg/itaque-tempore-exercitationemjs/@taktikorg/itaque-tempore-exercitationem/master/assets/rainbow.png)

# Notes

Inspired from [frisby](https://docs.frisbyjs.com/) and [pact](https://docs.pact.io).

## Support

Like this project! Star it on [Github](https://github.com/taktikorg/itaque-tempore-exercitationem/stargazers) and follow on [Twitter](https://twitter.com/@taktikorg/itaque-tempore-exercitationemjs). Your support means a lot to us.

## Contributors

If you've ever wanted to contribute to open source, and a great cause, now is your chance! See the [contributing docs](https://github.com/taktikorg/itaque-tempore-exercitationem/blob/master/CONTRIBUTING.md) for more information.

Thanks to all the people who contribute.

<a href="https://github.com/taktikorg/itaque-tempore-exercitationem/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=@taktikorg/itaque-tempore-exercitationemjs/@taktikorg/itaque-tempore-exercitationem" />
</a>
<br />