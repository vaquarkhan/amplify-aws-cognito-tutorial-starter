## Hexal Energy app

This is a starter ReactJS UI for my 'Create a Serverless App' tutorial series.

## Application Info

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br>
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br>
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br>
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br>
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br>
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify

---------------------------------------------------------------
Tutorial:

- https://www.youtube.com/watch?v=EaDMG4amEfk
- https://www.youtube.com/watch?v=2SaO1Pvah2k
- https://www.youtube.com/watch?v=-K85GjI5SQ0
- https://www.youtube.com/channel/UCTJxrTdQWFGtKxTeincy9uA

Documentation 

- https://docs.aws.amazon.com/amplify/
- https://aws-amplify.github.io/
- https://github.com/dabit3/awesome-aws-amplify

--------------------------------------------------------------
cd dir 


npm i


npm i aws-amplify

npm run start


Open browser http://localhost:3000/


--------------------------------------------------------------
### Cognito Userpool

Amazon Cognito user pools implements ID, access, and refresh tokens as defined by the OpenID Connect (OIDC) open standard:

## - The ID Token contains claims about the identity of the authenticated user such as name, email, and phone_number.

The ID token is a JSON Web Token (JWT) that contains claims about the identity of the authenticated user such as name, email, and phone_number. You can use this identity information inside your application. The ID token can also be used to authenticate users against your resource servers or server applications. When an ID token is used outside of the application against your web APIs, you must verify the signature of the ID token before you can trust any claims inside the ID token. See Verifying a JSON Web Token.

The ID token expires one hour after the user authenticates



			{
				  "sub": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
				  "aud": "xxxxxxxxxxxxexample",
				  "email_verified": true,
				  "token_use": "id",
				  "auth_time": 1500009400,
				  "iss": "https://cognito-idp.us-east-1.amazonaws.com/us-east-1_example",
				  "cognito:username": "janedoe",
				  "exp": 1500013000,
				  "given_name": "Jane",
				  "iat": 1500009400,
				  "email": "janedoe@example.com"
				  }


## - The Access Token grants access to authorized resources.


The user pool access token contains claims about the authenticated user, but unlike the ID token, it does not include identity information. The primary purpose of the access token is to authorize API operations in the context of the user in the user pool. For example, you can use the access token to grant your user access to add, change or delete user attributes. The access token can also be used with any of your web APIs to make access control decisions and authorize operations for your users.

The access token is also represented as a JSON Web Token (JWT). The header for the access token will have the same structure as the ID token, but the key ID (kid) will be different because different keys are used to sign ID tokens and access tokens. As with the ID token, you must first verify the signature of the access token in your web APIs before you can trust any of its claims. See Verifying a JSON Web Token.


The access token expires one hour after your user successfully authenticates

			
			{
				"auth_time": 1500009400,
				"exp": 1500013000,
				"iat": 1500009400,
				"iss": "https://cognito-idp.us-east-1.amazonaws.com/us-east-1_example",
				"scope": "aws.cognito.signin.user.admin",
				"sub": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
				"token_use": "access",
				"username": "janedoe@example.com"
			}


## - The Refresh Token contains the information necessary to obtain a new ID or access


You can use the refresh token to retrieve new ID and access tokens.

By default, the refresh token expires 30 days after your app user signs in to your user pool. When you create an app for your user pool, you can set the app's refresh token expiration (in days) to any value between 1 and 3650.

The Mobile SDK for iOS and the Mobile SDK for Android automatically refresh your ID and access tokens if there is a valid (non-expired) refresh token present, and the ID and access tokens have a minimum remaining validity of 5 minutes. If the refresh token is expired, your app user must reauthenticate by signing in again to your user pool.

Note

The Mobile SDK for Android offers the option to change the minimum validity period of the ID and access tokens to a value between 0 and 30 minutes. See the setRefreshThreshold() method of CognitoIdentityProviderClientConfig in the AWS Mobile SDK for Android API Reference.

Your user's account itself never expires, as long as the user has logged in at least once before the UnusedAccountValidityDays time limit for new accounts.

To use the refresh token to get new ID and access tokens with the user pool API, use the AdminInitiateAuth or InitiateAuth methods. Pass REFRESH_TOKEN_AUTH for the AuthFlow parameter. The authorization parameters, AuthParameters, are a key-value map where the key is "REFRESH_TOKEN" and the value is the actual refresh token. Amazon Cognito responds with new ID and access tokens.



 "App can use the GlobalSignOut API to allow individual users to sign themselves out from all devices. Typically an app would present this option as a choice, such as Sign out from all devices".


-------------------------------------------------
## id_token vs access_token

The id_token is for your application to process, so you can get all the personal details for your user, like their name, age, email address etc. Generally speaking you shouldn't send this token anywhere else as it contains sensitive user data.

The access_token is used to call other 'external' services (and by external I include other AWS services - these are often called over http). It provides service access authorisation for your user without having to include their personal details.

###  Token vs SessionToken vs SyncSessionToken


- Token: This is a OpendId Connect compliant id token issued by Cognito Identity which asserts the users identity in a signed and verifiable way. Consider this token as a digital identity card which can be used by clients to verify the identity of users. You can refer to cognito API documentation for details on how to obtain this token and this documentation for more details on how to validate this token as a client.

- SessionToken: This token is issued by the service as a descriptor of users AWS session along with the temporary AWS credentials. Cognito calls STS on your behalf and returns the temporary credentials returned. When using other AWS resources using the issued temporary credentials, this token should be a part of the passed temporary credentials. Refer to cognito API reference and STS documentation for more details.

- SyncSessionToken: Is an identitfier issued by Cognito Sync service after initializing a sync operation. This sync operation is used as a unit for Cognito sync pricing. A sync operation is marked complete when you perform a successful write/update records using this token or this token expires.



- https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-tokens-with-identity-providers.html

-------------------------------------------------

### Synch congnito with RDS 

Lambda Resolvers: https://docs.aws.amazon.com/appsync/latest/devguide/tutorial-lambda-resolvers.html

AppSync Auth with User Pools: https://docs.aws.amazon.com/appsync/latest/devguide/security-authorization-use-cases.html

