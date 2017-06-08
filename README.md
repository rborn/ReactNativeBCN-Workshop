This repo holds the files and the summary for the [React Native Barcelona Workshop](https://www.meetup.com/React-Native-Barcelona/events/240051555/)

#### Tooling ####

[Expo](https://expo.io/) - install the app on your device (iOS or Android)

[create-react-native-app](https://github.com/react-community/create-react-native-app) - install globally the CRNA (create-react-native-app) node module


~~~
npm install -g create-react-native-app
~~~

To create a new project run in a terminal

~~~
create-react-native-app MyApp
cd MyApp
npm start
~~~

At this moment you should have a QR code and be able to scan it with Expo to start the app on your device.

Download the `App.js`,`coffeeShopStyle.js` and `data.js` files in the root of your project (you will need to overwrite the old `App.js`), Expo should reload 
the app and present the final stage we finished the workshop with (the list with the coffee shops)


#### Summary ####

- Small introduction to ReactNative, how it works (UI is native, logic is executed in a separated JS thread)
- Bridge crossing by serialising data between the UI and the JS threads (this is bad for speed so keep it at a minimum)
- Small introduction to the JSX syntax -  it's just javascript with some xml in the render part :)

**Components detailed explanation**

We explained the reason behind component driven architecture (good encapsulation, easy to maintain, easy porting to various platforms because the rendering is handeled outside the comonent itself)

**Main attributes of a component:**

 - `render()` - the method that renders the UI and where the xml resides
 - `props` - the properties (**read only**) we send to the component and which are used to initialize it
 - `state` - this is what keeps track of the changes inside a component and we use when our component is not static.
 
**Things to know about `state`**

- every change you do the `state` will force a render (except the case where you use `shouldComponentUpdate()` to allow or not a re-render)
- you cannot alter the `state` directly, you need to use `setState()` otherwise the component won't know there was a change
- it's set **async** (for optimization reasons, remember we try to avoid crossing the bridge too many times, so it's batched if there are many `setState()` calls), so if you need to use it after you set it do it in the `setState()` callback.
- you initialize the `state` in the `constructor()` method of the component

**Optimizations we need to have in mind**

- `shouldComponentUpdate()` is used to let the component know if it has to re-render the UI. You can compare the previous and the next state or implement any other logic that will render only if needed.
- you can evaluate expressions in the xml part, to render only the elements that are necessary.

**Some subjects from the questions**

- the spread operator `...` is very well explained [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator) and more specific for [our use case](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator#Spread_in_object_literals)
- `{someVariable}` in xml will evaluate that variable (it works similar to a templating system)
- for routing (navigation) we suggested https://reactnavigation.org/ (easy to use, pure JS, might be slower) and https://wix.github.io/react-native-navigation/#/ (difficult to implement as it needs to alter native code, but very fast and in line with each platform UI guidelines)
- *dumb* components (or stateless) - where possible use a component that doesn't have any logic in it and there is no need to re-render. [This is a more advanced article if you want to go deeper](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0).


#### Many thanks to [TravelPerk](https://travelperk.com/) for hosting the event! ####






