
**Prerequisites:** 
* [Node 12](https://nodejs.org/)+
* [Java 11](https://adoptopenjdk.net/)+
* An [Okta Developer Account](https://developer.okta.com/signup/)

> [Okta](https://developer.okta.com/) has Authentication and User Management APIs that reduce development time with instant-on, scalable user infrastructure. Okta's intuitive API and expert support make it easy for developers to authenticate, manage and secure users and roles in any application.

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
* [License](#license)

## Getting Started

To install this example application, run the following commands:

```bash
git clone https://github.com/IBNAHMADMOHAMED1/kotlinWithOkta.git
cd kotlinWithOkta
```

This will get a copy of the project installed locally. To install all of its dependencies and start each app, follow the instructions below.

### Spring Boot Configuration

To create a new OIDC app for Spring Boot on Okta:

1. Log in to your developer account, navigate to **Applications**, and click on **Add Application**.
2. Select **Web** and click **Next**. 
3. Give the application a name and add `http://localhost:8080/login/oauth2/code/okta` as a login redirect URI. 
4. Click **Done**.

Create an `okta.env` file and copy your settings into it.

```bash
export OKTA_OAUTH2_ISSUER=https://{yourOktaDomain}/oauth2/default
export OKTA_OAUTH2_CLIENT_ID={yourClientId}
export OKTA_OAUTH2_CLIENT_SECRET={yourClientSecret}
```

**NOTE:** The value of `{yourOktaDomain}` should be something like `dev-123456.okta.com`. Make sure you don't include `-admin` in the value!

Start your Spring Boot app by navigating to the `notes-api` directory, sourcing this file, and starting your app.

```bash
cd notes-api
source okta.env
./gradlew bootRun
```

### Angular Configuration

To create a new OIDC app for Angular on Okta:

1. Log in to your developer account, navigate to **Applications**, and click on **Add Application**.
3. Select **Single-Page App** and click **Next**. 
4. Give the application a name, set the login redirect URI to `http://localhost:4200/callback`, and click **Done**.

Copy the `issuer` and `clientId` into `notes/src/app/auth-routing.module.ts`.

```typescript
const oktaConfig = {
  issuer: 'https://{yourOktaDomain}/oauth2/default',
  redirectUri: window.location.origin + '/callback',
  clientId: '{yourClientId}',
  pkce: true
};
```

Navigate into the `notes` folder and run:
 
```bash
npm install && npm start
```

Open your browser to <http://localhost:4200>, log in, and create notes to your hearts content!

## Links

This example uses the following open source libraries from Okta:

* [Okta Spring Boot Starter](https://github.com/okta/okta-spring-boot)
* [Okta Angular SDK](https://github.com/okta/okta-oidc-js/tree/master/packages/okta-angular)

## Help

No help 

## License

Apache, see [LICENSE](LICENSE).
