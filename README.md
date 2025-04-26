## https://github.com/auth0-samples/auth0-react-samples -> sample web login with Auth0
![preview](https://snipboard.io/knZ274.jpg)

Step 1: git clone https://github.com/auth0-samples/auth0-react-samples
```
cd Sample-01
```
Step 2:
```
rename auth_config.json.example -> auth_config.json
```
Change content like
```
{
  "domain": "auth0.codteam.net",
  "clientId": "rOuPxvYf0f6c9s5mAykeYEDOrL1e2hAg",
  "audience": "https://dev-e86ia3wmik2op64x.us.auth0.com/api/v2/"
}
```
![domain](https://snipboard.io/oVU3sA.jpg)
![clientId](https://github.com/user-attachments/assets/d9c50fb5-e7f9-4b6b-8da5-4cd2690bffaa)
![audience](https://github.com/user-attachments/assets/c518dd94-1ac3-4f88-95ea-4f762fec4c1f)

Step 3:
```
yarn install
```
Step 4:
```
yarn dev
```

---
## https://github.com/auth0-samples/auth0-acul-react-boilerplate -> build custom template cho Login
Step 1: 
```
git clone https://github.com/auth0-samples/auth0-acul-react-boilerplate
```
Step 2: Change content file `src/screens/loginId/index.tsx`
```
import { LoginId } from '@auth0/auth0-acul-js';
import { useState } from 'react';

export const LoginIdScreen = () => {
  const loginManager = new LoginId();
  const [email, setEmail] = useState('');

  return (
    <div className="w-[100vw] min-h-screen flex items-center justify-center bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
      <div className="max-w-md w-full space-y-6 bg-white p-8 rounded-lg shadow-md">
        <input
          type="email"
          placeholder="Enter your email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
          className="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
        />

        <button 
          className="w-full flex justify-center py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-black bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
          onClick={() => loginManager.login({ username: email })}
        >
          Continue
        </button>

        {loginManager.transaction.alternateConnections?.map(({ name, strategy }) => (
          <button
            key={name}
            className="w-full flex justify-center py-2 px-4 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
            onClick={() => loginManager.socialLogin({ connection: name })}
          >
            Continue with {strategy}
          </button>
        ))}
      </div>
    </div>
  );
};

export default LoginIdScreen
```

```
cd auth0-acul-react-boilerplate
npm i
npm install @auth0/auth0-acul-js

npm run build
npx http-server dist -p 8080
```
---
## config Authentication Profile
![image](https://github.com/user-attachments/assets/5a645f09-da68-44ee-b5f5-a85da02aa675)

---
## Update render settings for a screen
https://auth0.com/docs/api/management/v2/prompts/patch-rendering

Get token:
![image](https://github.com/user-attachments/assets/09d2178d-1f71-4fd8-9a1c-799be9e54928)
![image](https://github.com/user-attachments/assets/9cbda95c-1354-4da6-8249-66dda713c8ca)

Set API Token
![image](https://github.com/user-attachments/assets/22d7c0e6-7e37-4e1e-959d-15e2b34a451a)

![image](https://github.com/user-attachments/assets/8bf12cdc-70d8-4433-bfe7-b630bf08a432)

body config
```
{
  "rendering_mode": "advanced",
  "context_configuration": [
    "screen.texts"
  ],
  "default_head_tags_disabled": false,
  "head_tags": [
    {
      "attributes": {
        "async": true,
        "defer": true,
        "integrity": [
          "ASSET_SHA"
        ],
        "src": "http://127.0.0.1:8080/index.js"
      },
      "tag": "script"
    },
    {
      "attributes": {
        "href": "http://127.0.0.1:8080/index.css",
        "rel": "stylesheet"
      },
      "tag": "link"
    }
  ]
}
```
---
## Test login
![image](https://github.com/user-attachments/assets/8f6b9bb5-d429-41c1-ad99-270999224e06)
![image](https://github.com/user-attachments/assets/a3cdb881-6fbd-48ff-baab-07fc33abdcbe)

## Config pages
- https://auth0.com/docs/customize/login-pages/advanced-customizations/getting-started/configure-acul-screens
- https://auth0.com/docs/customize/login-pages/advanced-customizations/reference
