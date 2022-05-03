# react-custom-hooks-state-management
Examples of simple state management using react custom hooks.

## Types of state

It is helpful to consider the different types of state that may be implemented as each type of state has its own requirements.

### 1. Server state

**Server state** is state that is persisted to a server via network communication, often over WSS or HTTPS protocols.

#### Stratagies

- [useSWR](https://swr.vercel.app/) is a powerful package that comes with several nifty [features](https://swr.vercel.app/#features) for getting data from the server in an efficient way thanks to the built-in cache and request deduplication.
- The [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) is a good way to interact with the server for non-get requests (PUT/POST/DELETE).

### 2. Route state

**Route state** is state that is persisted to the URL as path parameters or query parameters.

#### Stratagies

- [useQueryParam](https://www.npmjs.com/package/use-query-param) makes it incredibly easy to manage query parameter state. The default react router can be used for path parameter state.

### 3. Client state

**Client state** is generally used to control the interactive states of an application such as modals or themes.

#### Stratagies

- [useState](https://reactjs.org/docs/hooks-state.html) is the default state management option provided by React and it works wonderfully. In the case where you want to share the state generated by useState across 2 or more components, simply move the useState hook into a custom hook and wrap it with [useBetween](https://www.npmjs.com/package/use-between).
- [useLocalStorage](https://www.npmjs.com/package/use-local-storage) is a helpful library for persisting state to the browser.

## Implementation

For each type of state (and possibly for each resource), create a [custom hook](https://reactjs.org/docs/hooks-custom.html) and use the state management stratagy that makes the most sense for the given use-case. 

## Reasoning

There are many options for developers when it comes to state management ([Top 6 React state management libraries for 2022](https://blog.openreplay.com/top-6-react-state-management-libraries-for-2022)), but they all come with pros and cons. I've tried a few out, the only one that I've ever really fully implemented was redux. I can apprecaite some of the benefits, but imo they didn't out weigh the complexity–there is quite a bit of boilerplate code. Modifying the state meant updating about 4 separate file depending on how the actions/dispatchers/reducers were organized. And then, this became slightly more complex if redux-saga or redux-thunk packagers were used to create syncronous server state management. So, after I gave up on redux, I dove into a number of blogs that weighed the pros and cons of the different options. It was overwhelming. I tried a few out on hello-world apps, but I didn't find what I was looking for. I was looking for simplicity/flexibility/readability. React hooks had recently been launched and somehow I decided to try managing state from a custom React hook... And it was amazing. Using React hooks such as useState along with some lightweight packages, I was able to create state management that was very simple, very flexible and very readable. 

I've implemented this in two small-to-medium sized apps so far and things have gone wonderfully. So, that is why I've put together this Github repository with some examples.

## ToDo

[ ] Gather performance information

## Resoures

- [Web Applications Client-side State Management](https://medium.com/@saransh.ahlawat94/web-applications-client-side-state-management-97e1a27006ee)
