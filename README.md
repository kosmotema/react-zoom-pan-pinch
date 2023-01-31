# react-zoom-pan-pinch

[![NPM](https://img.shields.io/npm/v/@kosmotema/react-zoom-pan-pinch.svg)](https://www.npmjs.com/package/@kosmotema/react-zoom-pan-pinch)
![npm bundle size](https://img.shields.io/bundlephobia/minzip/@kosmotema/react-zoom-pan-pinch)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
![NPM](https://img.shields.io/npm/l/@kosmotema/react-zoom-pan-pinch)
![npm](https://img.shields.io/npm/dm/@kosmotema/react-zoom-pan-pinch)
![GitHub stars](https://img.shields.io/github/stars/kosmotema/react-zoom-pan-pinch?style=social)

> Super fast and light react npm package for zooming, panning and pinching html
> elements in easy way
>
> Also supports working in Web Components and Shadow DOM

- [Demo](https://kosmotema.github.io/react-zoom-pan-pinch/?path=/story/examples-big-image--big-image)
- [Docs](https://kosmotema.github.io/react-zoom-pan-pinch/?path=/story/docs-props--page)

## Features

- :rocket: Fast and easy to use
- :factory: Light, without external dependencies
- :gem: Mobile gestures, touchpad gestures and desktop mouse events support
- :gift: Powerful context usage, which gives you a lot of freedom
- :wrench: Highly customizable
- :crown: Animations and Utils to create own tools

## Install

```bash
npm install --save react-zoom-pan-pinch
```

or

```bash
yarn add @kosmotema/react-zoom-pan-pinch
```

or

```bash
pnpm add @kosmotema/react-zoom-pan-pinch
```

## Usage

```jsx
import React, { Component } from "react";

import {
  TransformWrapper,
  TransformComponent,
} from "@kosmotema/react-zoom-pan-pinch";

import "@kosmotema/react-zoom-pan-pinch/dist/index.css";

class Example extends Component {
  render() {
    return (
      <TransformWrapper>
        <TransformComponent>
          <img src="image.jpg" alt="test" />
        </TransformComponent>
      </TransformWrapper>
    );
  }
}
```

or

```jsx
import React, { Component } from "react";

import {
  TransformWrapper,
  TransformComponent,
} from "@kosmotema/react-zoom-pan-pinch";

import "@kosmotema/react-zoom-pan-pinch/dist/index.css";

class Example extends Component {
  render() {
    return (
      <TransformWrapper
        initialScale={1}
        initialPositionX={200}
        initialPositionY={100}
      >
        {({ zoomIn, zoomOut, resetTransform, ...rest }) => (
          <React.Fragment>
            <div className="tools">
              <button onClick={() => zoomIn()}>+</button>
              <button onClick={() => zoomOut()}>-</button>
              <button onClick={() => resetTransform()}>x</button>
            </div>
            <TransformComponent>
              <img src="image.jpg" alt="test" />
              <div>Example text</div>
            </TransformComponent>
          </React.Fragment>
        )}
      </TransformWrapper>
    );
  }
}
```

or

```tsx
import React, { useRef } from "react";
import {
  TransformWrapper,
  TransformComponent,
  ReactZoomPanPinchRef,
} from "@kosmotema/react-zoom-pan-pinch";

import "@kosmotema/react-zoom-pan-pinch/dist/index.css";

const Component = () => {
  const transformComponentRef = useRef<ReactZoomPanPinchRef>(null!);

  const zoomToImage = () => {
    const { zoomToElement } = transformComponentRef.current;
    zoomToElement("imgExample");
  };

  const Control = ({
    zoomIn,
    zoomOut,
    resetTransform,
  }: ReactZoomPanPinchRef) => (
    <>
      <button onClick={() => zoomIn()}>+</button>
      <button onClick={() => zoomOut()}>-</button>
      <button onClick={() => resetTransform()}>x</button>
    </>
  );

  return (
    <TransformWrapper
      initialScale={1}
      initialPositionX={200}
      initialPositionY={100}
      ref={transformComponentRef}
    >
      {(utils) => (
        <>
          <Control {...utils} />
          <TransformComponent>
            <img src="image.jpg" alt="test" id="imgExample" />
            <div onClick={zoomToImage}>Example text</div>
          </TransformComponent>
        </>
      )}
    </TransformWrapper>
  );
};
```

## License

MIT © [prc5](https://github.com/prc5), [kosmotema](https://github.com/kosmotema)
