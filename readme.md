# @nosferatu500/electron-google-oauth2
> Library that manages Google OAuth2 authentication for your [Electron](https://www.electronjs.org) app.

## Install
```
// npm
$ npm install --save @nosferatu500/electron-google-oauth2
// yarn
$ yarn add @nosferatu500/electron-google-oauth2
```

## Usage

### Access Token
```typescript
import ElectronGoogleOAuth2 from '@nosferatu500/electron-google-oauth2';

app.on('ready', () => {
  const myApiOauth = new ElectronGoogleOAuth2(
    'CLIENT_ID',
    'CLIENT_SECRET',
    ['https://www.googleapis.com/auth/drive.metadata.readonly']
  );

  myApiOauth.openAuthWindowAndGetTokens()
    .then(token => {
      // use your token.access_token
    });
});
```

### Refresh Token
```typescript
import ElectronGoogleOAuth2 from '@nosferatu500/electron-google-oauth2';

app.on('ready', () => {
  const myApiOauth = new ElectronGoogleOAuth2(
    'CLIENT_ID',
    'CLIENT_SECRET',
    ['https://www.googleapis.com/auth/drive.metadata.readonly']
  );
  
  const refreshToken = \\ Read the saved refresh token
  
  if(refreshToken) {
    myApiOauth.setTokens({ refresh_token: refreshToken });
  } else {
    myApiOauth.openAuthWindowAndGetTokens()
      .then(token => {
        // save the token.refresh_token secured to use it the next time the app loading
        // use your token.access_token
      });
  }
});
```

### Requires with plain JavaScript

```js
const ElectronGoogleOAuth2 = require('@nosferatu500/electron-google-oauth2').default;
new ElectronGoogleOAuth2(CLIENT_ID, CLIENT_SECRET, SCOPES_LIST);
```

## License
MIT
