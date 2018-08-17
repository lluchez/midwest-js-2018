[MidwestJS 2018](http://midwestjs.com/#/schedule)

# Automated testing with [Cypress.io](https://www.cypress.io/)
[Slides](https://mike-plummer.github.io/cypress-presentation/)

Selenium issues: outdated APIs, old browsers, cross-browser compatibility, flaky tests
- Cypress:
  - runs inside the browser and replaces the browser <-> app interface
  - auto-waiting to reduce flake
  - debuggable (you can debug Cypress as well as the browser DOM)
  - snapshot at any moment for Time Travel (Video for CI, full DOM inspection with the local tool)
  - able to mock the clock (to simulate session timeouts) and network requests (+ send HXR calls)
  - limitations
    - single browser tab, single domain
    - more difficult to use existing common/server-side code
    - currently supports only Chrome/Chromium (but will be extended: Firefox, Safari, Edge, but never IE)
  - is Promise-based (chaining actions is the preferred way to ensure actiosn are completed before moving to the next)
  - supports aliasing for selectors
  - ability to create re-usable sequences of commands
  - works with use Mocka/Chai/Sinon
  - [Using async and await](https://medium.com/@NicholasBoll/cypress-io-using-async-and-await-4034e9bab207) instead of promises


# Harness the Power of ASTs using jscodeshift
[Slides](https://github.com/lund0n/jscodeshift-midwestjs)
- Used for Code maintenance
- [Developer Tool](http://astexplorer.net)
- Less error prone that manual changes
- Babel, ESLint, Prettier, IglifyJS, Webpack are using ASTs
- [react-codemod](https://github.com/reactjs/react-codemod): to help update React APIs
- Video: [Rename Unsafe Lifecycle Hooks with react-codemod](https://www.youtube.com/watch?v=UqLh2K9j-wk)


# How to identify bad third-parties on your pages
[Slides](https://docs.google.com/presentation/d/1D7iUBYJu4CZb1B-eHvkPT7JztMOwRQo2Co1d-EDnV94/edit?usp=sharing)
- What can go wrong? Page break, Performance issues, [Privacy/security](https://docs.google.com/presentation/d/1D7iUBYJu4CZb1B-eHvkPT7JztMOwRQo2Co1d-EDnV94/edit#slide=id.g2b4f799ae8_0_7), harder to debugging your own code.
- When using 3rd-party code means that you're bringing in code you don't have control over to your page
- Using local overrides (Chrome 65+) to [update/remove code](https://docs.google.com/presentation/d/1D7iUBYJu4CZb1B-eHvkPT7JztMOwRQo2Co1d-EDnV94/edit#slide=id.g2a07e7532e_1_7) [demo](https://docs.google.com/presentation/d/1D7iUBYJu4CZb1B-eHvkPT7JztMOwRQo2Co1d-EDnV94/edit#slide=id.g2a07e7532e_1_29)
- Using iframe for external dependencies so they can't read cookies neither interact with the page, only their iframe
- Sanboxing Iframes for enhanced security
- Using a lib like [Freeze.js](https://github.com/cvazac/freeze.js) to freeze constructors, methods, and properties


# Forgot Password? Yes I Did!
[Slides](https://www.slideshare.net/JoelLord4/forgot-password-yes-i-did), [repo](https://github.com/joellord/secure-spa-auth0)
- 1961: introduction of password at MIT
- costs 70$ every time a user has to call help desk (study result)
- [Data Breach Statistics](https://breachlevelindex.com/)
- More social media presence => easier social engineering. Avoid mechanism with social questions
- More computing power means it's easier to crack passwords
- Users will always be the weakiest link [post it](assets/hawaii_false_alarm.png)
- 23% of users admit having only one password. We all hate passwords!
- What can we do?
  - OAth
  - Delegate (Gmail, Facebook, etc)
  - MFA
  - Forget Password mechanism
  - Password Managers
  - YubiKeys (WebAuthn API)
  - Biometrics. **You can't change your biometrics if there is a leak!!!**
  - Magic links (will send an email to your email address, cf Slack, Amazon)


# Shields Up! Security and React Apps
[Slides](https://github.com/ZacharyKlein/shields-up-securing-react-apps)
- Run `npm audit`
- Potential loopholes for XSS with React: `href` and `formaction`.
- Once data makes it to the UI, it's too late to secure it.
- Authorization needs to be checked at every endpoint.
- Auth0 and Okta are OAuth providers easy to use with React


# I don't Care About Security and Neither Should You
[Slides](https://t.co/Wqc29sw0Gp), [repo](https://github.com/joellord/secure-spa-auth0)

OAuth
- [JWT.io](https://jwt.io/) to parse JWT tokens
- JWT tokens ahve a header, content and signature.
- Do not store sentitive information in a JWT tokens as base64 encoded, but not encrypted!
- express-jwt: JWT middleware token validator
- Do not store token into Local Storage, use cookies instead (but it is vulnerable to CSRF, cf `Shields Up! Security and React Apps` talk) or a store
- Reset token should be stored in a more permanent way like on the API database.
- `app.get('*', () => {})` to catch all 404

OpenID Connect
- Allowing scopes (openid, profile, email, address, phone)
- playground for developers to test and work with OpenID Connect: [OpenIDConnect.net](https://openidconnect.net/)


# Using JavaScript to write Native Applications/SDK's for iOS, Android and the Web
[Slides](https://www.slideshare.net/DerekAnderson20/using-javascript-to-write-native-mobile-applications)

Advantages of using JS framework (like React Native):
- Dynamically updatable UI. No need to repush to the App/Play Store.
- Less friction with merchants

[Syr](https://github.com/syrjs/core) ([main page](https://syr.js.org/)), light-weight version of React Native by **Paypal** (doesn't include React)
  - Works for iOS/Android/Web, with the same code
  - Syr-push
  - Syr-bus (for communication between components/iframes)


# Bad Software
- No one read user manuals
- Make sure to involve users
- Do not build over-complicated UI with too many controls
- White-board designing can save time and fix issue before head
- [Kano model](https://en.wikipedia.org/wiki/Kano_model). Basic needs, Fully implemented, Delighters


# Selling your Boss on GraphQL
[Slides](https://r-walsh.github.io/graphql-tech-talk/assets/player/KeynoteDHTMLPlayer.html)
- Apollo can check types
- DataLoader (from Facebook) to avoid N+1
- Framework can have caching mechanisms, as well as monitoring/profiling tools
- Apollo Link Rest (currently in beta) to proxy requests
- BAAS (BackEnd As A Service): GraphCool, GraphCMS, AWS AppSync, Hasura
- GitHub Facebook, Shopify, Credit Karma, Walmart have adopted GraphQL


# Pack your Callbags! A new spec for Streams
[Slides](https://github.com/lund0n/callbags-midwestjs)

[Callbags](https://github.com/callbag/callbag)

[Callbags Basics](https://github.com/staltz/callbag-basics) Tiny and fast reactive/iterable programming library

For unifying Push and Pull operations
- `from([1,2,3,4,5]).pipe(filter(x => x % 2 === 0), map(x => x+5), scan((acc,curr) => ac+curr)).subscribe(x => console.log(x))`
- 0: start (sent by the producer), 1: data, 2: stop (sent by the consummer or producer)


# All aboard the Hypertrain: Blockchains or bust (Blockchain for Fun and Profit)
[Slides](https://github.com/delventhalz/pirate-talk)
- Decentralized algorithmic trust


## See also
- SailsJS
- [Webtask](http://bit.ly/mwjs-webtask)
- [Transpile to JS](https://docs.google.com/presentation/d/11Ep1ES-J253HOBOWw3iHg0qaXLf6lzxYWWeuxZSB-xQ/edit#slide=id.g742e3e7cd_1_33)
- [redux-persist](https://github.com/rt2zz/redux-persist) to persist and rehydrate Redux store
- Redux Sagas


## Other slides
- [React Workshop](https://react-training.objectpartners.com/)
- [WebAssembly and Rust](https://GitHub.com/kimtuck/webassembly)
- [Blazing Fast UI Dev with StoryBook](https://slides.com/caitecoll/midwestjs2018#/) [repo](https://github.com/meastes/library-storybook)
- [Gatsby: Static Site Generation with React](https://www.gatsby.dustinschau.com/)
- [How Does JavaScript Math?](assets/how_does_javascript_math_2018_midwest_js.pdf) by Meara Charnetzki (similar talk than at WindyCityRails 2017)
- [Wicked Fast ⚡ Mobile Web](https://slides.today/decks/-LH9-K13Y-H5XF9wQQi8)
- [A Practical Approach to the Component Library Challenge](http://amlyhamm.com/talks/midwest-js-2018/#/)
- [Room with a Vue](https://github.com/ZacharyKlein/room-with-a-vue-midwestjs)
- [Intro to Vue.js: The Frontend Framework for Everyone!](https://github.com/ddanger/vue-basics) [Codepen Todo App](https://codepen.io/collection/DprzEK/)
- [Angular Test Dependency Injection](https://github.com/LMFinney/toh-pt6_20180521)
- [So you're doing Redux, but is your Data Safe?](https://tinyurl.com/midwestjs2018ImmutabilitySlide) [repo](https://github.com/LMFinney/toh-ngrx6-immutability) (Demonstrating ngrx immutability, Angular talk)
- [Vuex Demo](https://github.com/superMDguy/vuex-demo/)
