---
title: "NextJS SDK"
slug: "../next-sdk"
sidebar_position: 2
---

//SDK-TODO Rename to **Moralis NextJS SDK/Package**?

:::info overview
This guide will teach you how to **install** and **set up** the [**Moralis NextJS SDK**](https://github.com/MoralisWeb3/Moralis-JS-SDK/tree/main/packages/next).
:::

## Installation

To install the SDK, run the following commands:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
<TabItem value="npm" label="npm" default>

```shell
npm install @moralisweb3/next next next-auth react react-dom
```

</TabItem>
<TabItem value="yarn" label="yarn">

```shell
yarn add @moralisweb3/next next next-auth react react-dom
```
</TabItem>
</Tabs>

## Setting up

### Create environment variables file

Add a new `.env.local` file in your NextJS project's root and provide a `MORALIS_API_KEY` variable.

### Create API route

To use Moralis APIs in your NextJs project create a `pages/api/moralis/[...moralis].ts` file with the following code:
```js
import { MoralisNextApi } from "@moralisweb3/next";

export default MoralisNextApi({ apiKey: process.env.MORALIS_API_KEY });
```

:::tip
Instead of just passing the `MORALIS_API_KEY` to the `MoralisNextApi` object, you can also pass a `MoralisConfig` object with [additional configuration parameters](/web3-data-api/getting-started/moralis-sdks/javascript-sdk#configuration).
:::