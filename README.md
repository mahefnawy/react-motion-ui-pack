## React Motion UI Pack 0.3.1

[React Motion](https://github.com/chenglou/react-motion) is an amazing animation library for React. React Motion UI Pack tries to help ease entry level / common use cases with React Motion by providing a higher level way to work with it and create common UI transitions easier. If you need more complex animations I suggest using React Motion directly.

## Install

`npm install react-motion-ui-pack --save`

`bower install react-motion-ui-pack --save`

## Props
**component:** define the wrapping tag around the children passed in
**onlyChild:** useful if you only want to transition in/out 1 element rather than a list
**measure:** pass true to use React Measure and get child dimensions to use with your animations (note: you need to include React Measure on your own)
**appear:** Determines where the animation starts, pass true to default to leave or false for no animation on mount, accepts an object or boolean value
**enter:** The resting state of the animation
**leave:** The ending value of the animation

## Control where values are applied
If you decide to use a custom component as a child, `style` and `dimensions` props will be passed into that component for you to use however you want. If you don't pass anything, `<Transition />` will take care of applying the values for you to a `span` wrapper. This tag can be changed to any tag you need using the `component` prop provided on the `<Transition />` component.

## Quirks
When using auto width/height values, [React Measure](https://github.com/souporserious/react-measure) must be included in order to obtain proper dimensions to animate to.

## Example Usage

```javascript

import Transition from 'react-motion-ui-pack';

// Animate a modal
<Transition
  onlyChild={true}
  enter={{
    width: {val: 'auto'},
    height: {val: 'auto'},
    opacity: {val: 1},
    translateY: {val: 0, config: [400, 10]}
  }}
  leave={{
    width: {val: 0},
    height: {val: 0},
    opacity: {val: 0},
    translateY: {val: 250}
  }}
>
  {this.state.modalOpen &&
  <div key="modal" className="modal__content">
    // modal code
  </div>}
</Transition>

// Animate a list of items as they are added
<Transition
  component={'ul'}
  appear={true}
  enter={{
    height: {val: 'auto'},
    opacity: {val: 1},
  }}
  leave={{
    height: {val: 0},
    opacity: {val: 0},
  }}
>  
  {this.state.items.map(item => <li key={item.id}>{item.content}</li>)}
</Transition>
```

## Run Example

clone repo

`git clone git@github.com:souporserious/react-motion-ui-pack.git`

move into folder

`cd ~/react-motion-ui-pack`

install dependencies

`npm install`

run dev mode

`npm run dev`

open your browser and visit: `http://localhost:8080/`

## CHANGELOG
### 0.3.1
Updated to work with React Measure 0.1.2

Added prop `measure` to force use of Measure if wanting to use dimensions passed in

### 0.3.0
Fixed build for NPM, now points correctly to lib folder

Only dependant on React Measure if using width/height auto

### 0.2.5
Not exposed as an object anymore, but just as `Transition`

### 0.2.4
UI Pack not included anymore, will move into addons or something similiar

Fixed `appear` prop to work with elements coming in after initial mount

Uses React Measure 0.0.7 now

### 0.2.3
Optimized height & width calculation

Uses React Measure 0.0.6 now

### 0.2.2
Introduced `onlyChild` prop. If only animating one component pass `true` to get rid of the need for a wrapper component

A React Motion friendly object can now be passed to `appear` instead of just a boolean

### 0.2.1
Uses React Measure 0.0.5 now

### 0.2.0
Now dependent upon [React Measure](https://github.com/souporserious/react-measure)