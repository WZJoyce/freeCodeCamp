---
id: 587d824e367417b2b2512c58
title: Run Functional Tests on API Endpoints using Chai-HTTP
challengeType: 2
forumTopicId: 301593
---

## Description

<section id='description'>

As a reminder, this project is being built upon the following starter project on <a href="https://repl.it/github/freeCodeCamp/boilerplate-mochachai">Repl.it</a>, or cloned from <a href='https://github.com/freeCodeCamp/boilerplate-mochachai/'>GitHub</a>.

Mocha allows testing asyncronous operations. There is a small (BIG) difference. Can you spot it?

We can test our API endpoints using a plugin, called `chai-http`. Let's see how it works. And remember, API calls are asynchronous.

The following is an example of a test using `chai-http` for the `'GET /hello?name=[name] => "hello [name]"'` suite. The test sends a name string in a url query string (`?name=John`) using a `GET`request to the `server`. In the `end` method's callback function, the response object (`res`) is received and contains the `status` property. The first `assert.equal` checks if the status is equal to `200`. The second `assert.equal` checks that the response string (`res.text`) is equal to `"hello John"`.

```js
suite('GET /hello?name=[name] => "hello [name]"', function () {
  test("?name=John", function (done) {
    chai
      .request(server)
      .get("/hello?name=John")
      .end(function (err, res) {
        assert.equal(res.status, 200, "response status should be 200");
        assert.equal(
          res.text,
          "hello John",
          'response should be "hello John"'
        );
        done();
      });
  });
```

Notice the `done` parameter in the test's callback function. Calling it at the end without an argument is necessary to signal successful asynchronous completion.

</section>

## Instructions

<section id='instructions'>

Within `tests/2_functional-tests.js`, alter the `'Test GET /hello with no name'` test (`// #1`) to assert the `status` and the `text` response to make the test pass. Do not alter the arguments passed to the asserts.

There should be no name in the query; the endpoint responds with `hello Guest`.

</section>

## Tests

<section id='tests'>

```yml
tests:
  - text: All tests should pass
    testString: getUserInput => $.get(getUserInput('url') + '/_api/get-tests?type=functional&n=0').then(data => { assert.equal(data.state,'passed'); }, xhr => { throw new Error(xhr.responseText); })
  - text: You should test for 'res.status' == 200
    testString: getUserInput => $.get(getUserInput('url') + '/_api/get-tests?type=functional&n=0').then(data => { assert.equal(data.assertions[0].method, 'equal'); assert.equal(data.assertions[0].args[0], 'res.status'); assert.equal(data.assertions[0].args[1], '200');}, xhr => { throw new Error(xhr.responseText); })
  - text: You should test for 'res.text' == 'hello Guest'
    testString: getUserInput => $.get(getUserInput('url') + '/_api/get-tests?type=functional&n=0').then(data => { assert.equal(data.assertions[1].method, 'equal'); assert.equal(data.assertions[1].args[0], 'res.text'); assert.match(data.assertions[1].args[1], /('|")hello Guest\1/);}, xhr => { throw new Error(xhr.responseText); })
```

</section>

## Challenge Seed

<section id='challengeSeed'>

</section>

## Solution

<section id='solution'>

```js
/**
  Backend challenges don't need solutions, 
  because they would need to be tested against a full working project. 
  Please check our contributing guidelines to learn more.
*/
```

</section>
