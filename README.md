# Research - Collect as many properties as possible under globalThis

Trying to find the best way to collect as many properties as we can that are accessible under `globalThis`

> Visit https://weizman.github.io/global-this-props/ demo page and see results in the console

## Method 1

Calling `Object.getOwnPropertyDescriptors` on `globalThis`. Derived from:

```javascript
const target = globalThis;
Object.entries(Object.getOwnPropertyDescriptors(target));
```

Problem with this approach is that is assumes all properties on `globalThis` are its own properties, but in reality that's not the case.

In addition to its own properties, `globalThis` exposes own properties of `Object`, `EventTarget` and `Window` (for browsers) as well.

## Method 2

In this method we collect the properties of `globalThis`, `Object.prototype`, `EventTarget.prototype`, `Window.prototype` - all of which are accessible via `globalThis`

## Results

### NodeJS

<img width="350" alt="Screen Shot 2022-09-23 at 11 33 16" src="https://user-images.githubusercontent.com/13243797/191921837-9362f346-71a8-4906-9ec9-4f5d517f0f14.png">

### Chrome

<img width="1092" alt="Screen Shot 2022-09-23 at 11 33 46" src="https://user-images.githubusercontent.com/13243797/191921935-c8807236-8aea-4649-a485-e5239bfdef1d.png">

### Firefox

<img width="1092" alt="Screen Shot 2022-09-23 at 11 34 22" src="https://user-images.githubusercontent.com/13243797/191922037-88e375bf-d01a-4133-b137-01966da79d23.png">

### Safari

<img width="574" alt="Screen Shot 2022-09-23 at 11 34 45" src="https://user-images.githubusercontent.com/13243797/191922116-e8f23bf7-fbbe-4f7a-8658-87b0b3eaef9d.png">
