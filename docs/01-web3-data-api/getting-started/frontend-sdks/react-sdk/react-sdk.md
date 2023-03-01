---
title: "React SDK"
slug: "../react-sdk"
sidebar_position: 1
---

//SDK-TODO Rename to **Moralis React SDK/Package**?

:::info overview
This guide will teach you how to **install** and **set up** the [**Moralis React SDK**](https://github.com/MoralisWeb3/Moralis-JS-SDK/tree/main/packages/react).
:::

## Installation

To install the SDK, run the following commands:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
<TabItem value="npm" label="npm" default>

```shell
npm install @moralisweb3/react react react-dom
```

</TabItem>
<TabItem value="yarn" label="yarn">

```shell
yarn add  @moralisweb3/react react react-dom
```
</TabItem>
</Tabs>

## Setting up

To initialize and set up the SDK, add the following code to your React app:

```js
import React from "react";
import ReactDOM from "react-dom";
import { MoralisProvider, MoralisConfig } from "@moralisweb3/react";

const moralisConfig: MoralisConfig = {
  apiKey: "MORALIS_API_KEY",
};

ReactDOM.render(
  <MoralisProvider config={moralisConfig}>
    <App />
  </MoralisProvider>,
  document.getElementById("root"),
);
```

:::tip 
You can add [additional configuration parameters](/web3-data-api/getting-started/backend-sdks/moralis-js-sdk#configuration) to the **`MoralisConfig`** object.
:::