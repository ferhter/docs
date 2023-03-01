---
title: "Python SDK"
slug: "../python-sdk"
sidebar_position: 2
---

## Installation

<Tabs>
<TabItem value="pnpm" label="pnpm" default>

```shell
pnpm add moralis
```

</TabItem>
<TabItem value="pip" label="pip">

```shell
pip install moralis
```
</TabItem>
</Tabs>

## Initialization

To initialize the SDK, add the following code to your dapp:

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
<TabItem value="python" label="Python">

```python Python
import moralis

print(moralis.utils.web3_api_version(api_key='API_KEY_HERE'))

# it prints {'version': '0.0.53'}
```

</TabItem>
</Tabs>

Here, `Moralis.start`, with `apiKey` as a required input, will initialize the Moralis SDK.

Once the Moralis NodeJS SDK is initialized, you will be able to use all the powerful APIs provided by Moralis to build your dapps.

:::caution
Make sure to Store the `apiKey` Value Inside a `.env` File
:::

## Configuration

You can set the configuration for your Moralis instance when you call `Moralis.start(config)`. For example:

```javascript
Moralis.start({
  apiKey: "YOUR_API_KEY",
  formatEvmAddress: 'checksum',
  formatEvmChainId: 'decimal',
  logLevel: 'verbose'
})
```

Below, you can find the possible options for the configuration:

| Option           | Description                                                                                                          | Default       | Required |
| ---------------- | -------------------------------------------------------------------------------------------------------------------- | ------------- | -------- |
| apiKey           | Your secret Moralis ApiKey                                                                                           | `null`        | yes      |
| formatEvmAddress | Format style for evm addresses. Possible values: `'lowercase'`, `'checksum'`                                         | `'lowercase'` | no       |
| formatEvmChainId | Format style for chains. Possible values: `'decimal'`, `'hex'`                                                       | `'hex'`       | no       |
| logLevel         | Level of detail for log messages. Possible values: `'verbose'`, `'debug'`, `'info'`, `'warning'`, `'error'`, `'off'` | `'info'`      | no       |