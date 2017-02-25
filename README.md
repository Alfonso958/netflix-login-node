# Netflix Login

[![Circle CI](https://circleci.com/gh/johnf/netflix-login-node.svg?style=svg)](https://circleci.com/gh/johnf/netflix-login-node)
[![Coverage Status](https://coveralls.io/repos/johnf/netflix-login-node/badge.svg?branch=master&service=github)](https://coveralls.io/github/johnf/netflix-login-node?branch=master)

Login in to Netflix and provide cookies and encryption keys.

## Usage Notes

Please read the [Netflix Terms of Use](https://help.netflix.com/legal/termsofuse?locale=en&docType=termsofuse) before using this module.

## Installation

``` bash
npm install netflix-login
```

## Usage

``` javascript

import netflixLogin from 'netflix-login/login';
import netflixCrypto from 'netflix-login/crypto';

const options = {
  useCache: true,
  cachePath: 'tmp',
};
const username = 'johnf@inodes.org';
const password = 'secret';

netflixLogin.login(username, password, options)
  .then(authData => netflixCrypto.fetchCryptoKeys(authData, options))
  .then(data => console.error(data))
  .catch((error) => {
    console.error('ERROR');
    console.error(error);
  });
```

## Development

After checking out the repo, run `npm test` to run the tests.

To release a new version:

* npm test
* npm version major|minor|patch
* npm publish

This will run the tests, update the version, create a git tag for the version, push git commits and tags. Publish the module file to [npmjs.com](https://npmjs.com).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/johnf/netflix-login-node. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [ISC License](http://opensource.org/licenses/ISC).
