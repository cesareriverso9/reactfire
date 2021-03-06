# Upgrade from ReactFire v3 to v4

As announced in [Discussion 402](https://github.com/FirebaseExtended/reactfire/discussions/402), ReactFire v4 contains breaking changes. This guide details how to upgrade from v3 to v4.

**1. Get the latest version of ReactFire and Firebase**

```
npm i firebase@latest reactfire@latest

# or

yarn add firebase@latest reactfire@latest
```

**2. Initialize product SDKs and register them with ReactFire**

You'll need to explicitly initialize each Firebase product you use and pass the initialized SDK into a provider component. For example, if you use the `useUser` hook in a component, make sure a parent sets up Firebase Auth with the `AuthProvider` component. Here's a [code sample](./use.md#initialize-product-sdks-and-register-them-with-reactfire).

If you need to connect to the Local Emulator Suite, [check out this code sample](./use.md#connect-to-the-firebase-local-emulator-suite).

For times when you need to asynchronously initialize a product, like [accessing Firestore data offline](./use.md#access-data-offline) or [activating Remote Config](./use.md#initialize-fetch-and-activate), you can use hooks like `useInitFirestore` and `useInitRemoteConfig`. These hooks replace the preload functions.

**3. Update your Firebase code**

You'll need to [refactor to the modular style](https://firebase.google.com/docs/web/modular-upgrade#refactor_to_the_modular_style) of the new Firebase SDK. You can find per-product examples of using ReactFire with the new Firebase SDK [here](./use.md#using-reactfire).

> Need some samples? Check out the diffs between v3 and v4 for code in the `examples` directory of the ReactFire repo:
> - [Authentication](https://github.com/FirebaseExtended/reactfire/compare/v3.0.0...main#diff-c5694c5b02214b8cb9995c990ae8fd5c44cf93c151110276d0379d5197545db2)
> - [Firestore](https://github.com/FirebaseExtended/reactfire/compare/v3.0.0...main#diff-9e9ed90d3bbe78bed8b8f1451a90c012814b921262ac094b37d408f3467e83cf)
> - [Realtime Database](https://github.com/FirebaseExtended/reactfire/compare/v3.0.0...main#diff-defb854c7edb7dbe709574ada1ff638299a4d127fa366e67e95336bcab004411)
> - [Remote Config](https://github.com/FirebaseExtended/reactfire/compare/v3.0.0...main#diff-d746559c016f5bff411f3b86c7c72baa0f22d6b0e25cb69abd2dc878efca9eca)
> - [Storage](https://github.com/FirebaseExtended/reactfire/compare/v3.0.0...main#diff-4622df6233c1bd3749c3f861d2f84cbd92b7a788a0983b068a3e1cfce99419c7)