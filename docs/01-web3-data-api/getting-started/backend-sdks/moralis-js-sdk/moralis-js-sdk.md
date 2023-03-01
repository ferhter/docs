---
title: "JavaScript SDK"
sidebar_position: 1
---

//SDK-TODO Think about renaming the title to **Moralis JS SDK** or **Moralis SDK** but since we have more than one would go for first option.

:::info overview
This guide will teach you how to **install** and **set up** the [**Moralis-JS-SDK**](https://github.com/MoralisWeb3/Moralis-JS-SDK).
:::

:::note
The **Moralis-JS-SDK** is our main SDK.
:::

## Standard setup

:::info
In the majority of cases, this configuration will be sufficient.
:::

### Installation

To install the SDK, run the following commands:

<Tabs>
<TabItem value="npm" label="npm" default>

```shell
npm install moralis
```

</TabItem>
<TabItem value="yarn" label="yarn">

```shell
yarn add moralis
```
</TabItem>
</Tabs>

### Setting up

To initialize and set up the SDK, add the following code to your dapp:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
<TabItem value="javascript" label="Javascript" default>

```javascript
const Moralis = require("moralis").default;

await Moralis.start({
  apiKey: "YOUR_API_KEY",
  // ...and any other configuration
});
```

</TabItem>
<TabItem value="typescript" label="Typescript">

```typescript
import Moralis from "moralis";

await Moralis.start({
  apiKey: "YOUR_API_KEY",
  // ...and any other configuration
});
```
</TabItem>
</Tabs>

:::note
`Moralis.start` needs the [`apiKey`](/web3-data-api/get-your-api-key) as a required input.
:::

:::caution
It's good practice to store the `apiKey` in a `.env` file.
:::

### Configuration

Apart from the `apiKey`, you can pass **additional configuration parameters** when calling **`Moralis.start(config)`**. For example:

```javascript
Moralis.start({
  apiKey: "YOUR_API_KEY",
  formatEvmAddress: 'checksum',
  formatEvmChainId: 'decimal',
  logLevel: 'verbose'
})
```

Below you can find **all the required and optional parameters** for the configuration of the **Moralis instance**:

| Option           | Description                                                                                                          | Default       | Required |
| ---------------- | -------------------------------------------------------------------------------------------------------------------- | ------------- | -------- |
| apiKey           | Your secret Moralis ApiKey                                                                                           | `null`        | yes      |
| formatEvmAddress | Format style for evm addresses. Possible values: `'lowercase'`, `'checksum'`                                         | `'lowercase'` | no       |
| formatEvmChainId | Format style for chains. Possible values: `'decimal'`, `'hex'`                                                       | `'hex'`       | no       |
| logLevel         | Level of detail for log messages. Possible values: `'verbose'`, `'debug'`, `'info'`, `'warning'`, `'error'`, `'off'` | `'info'`      | no       |

## Advanced setup

:::info

Use the advanced setup if you want more control over what modules to add to Moralis. In most cases, you won't need to do this (and can use the umbrella `moralis` package as described above, as this is easier to use).

:::

### Installation

Instead of installing the `moralis` umbrella package, you can need to install the packages _you_ want to use. Please note that you **always** need to install the `@moralisweb3/core` package. 

Available packages:

- `@moralisweb3/core`
- `@moralisweb3/auth`
- `@moralisweb3/evm-api`
- `@moralisweb3/sol-api`
- `@moralisweb3/evm-utils`
- `@moralisweb3/sol-utils`

For example:

```bash npm2yarn
npm i @moralisweb3/core @moralisweb3/evm-api
```

### Setting up

To set up Moralis, you must register the modules to the core package at the top of your code (before any interaction with Moralis):

```javascript
import MoralisCore from '@moralisweb3/core';
import MoralisEvmApi from '@moralisweb3/evm-api';

const core = MoralisCore.create();
// Register all imported modules to the @moralisweb3/core module
core.registerModules([MoralisEvmApi]);
```



Then, initialize the app similarly to when using the umbrella `moralis` package. You only need to provide a configuration that is required by the packages. So, if you don't include an API package, you might not need to include the `apiKey`:

```javascript
core.start({
  apiKey: '<YOUR_API_KEY>',
  // ...and any other configuration
});
```



Now you can use any functionality from the installed modules. The only difference is that you need to call in your code:

```javascript
import MoralisEvmApi from '@moralisweb3/evm-api';
import { EvmChain } from '@moralisweb3/common-evm-utils';

const evmApi = core.getModule<MoralisEvmApi>(MoralisEvmApi.moduleName);
evmApi.block.getBlock({
    chain: EvmChain.ETHEREUM,
    blockNumberOrHash: "",
});
```



Instead of:

```javascript
import Moralis from 'moralis';
import { EvmChain } from '@moralisweb3/common-evm-utils';

Moralis.EvmApi.block.getBlock({
    chain: EvmChain.ETHEREUM,
    blockNumberOrHash: "",
});
```



Of course, you are free to combine the modules in a single object and use that in your dapp:

```javascript
// moralis.ts
import { MoralisCore } from '@moralisweb3/core';
import EvmApi from '@moralisweb3/evm-api';

const core = MoralisCore.create();
const evmApi = EvmApi.create(core);
core.registerModules([evmApi]);

export const Moralis = {
  EvmApi: evmApi,
};

// app.ts
import { Moralis } from './moralis/';
import { EvmChain } from '@moralisweb3/common-evm-utils';

Moralis.EvmApi.block.getBlock({
    chain: EvmChain.ETHEREUM,
    blockNumberOrHash: "",
});
```
