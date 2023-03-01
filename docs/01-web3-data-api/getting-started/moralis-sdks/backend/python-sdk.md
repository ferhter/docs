---
title: "Python SDK"
slug: "../python-sdk"
sidebar_position: 2
---

//SDK-TODO Think about renaming the title to **Moralis Python SDK**.

:::info overview
This guide will teach you how to **install** and **set up** the [**Moralis-Python-SDK**](https://github.com/MoralisWeb3/Moralis-Python-SDK).
:::

## Standard setup

:::info
In the majority of cases, this configuration will be sufficient.
:::

### Installation

To install the SDK, run the following commands:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

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

### Setting up

To initialize and set up the SDK, add the following code to your dapp:

```python Python
import moralis

print(moralis.utils.web3_api_version(api_key='API_KEY_HERE'))

# it prints {'version': '0.0.53'}
```

:::caution
It's good practice to store the `apiKey` in a `.env` file.
:::

//SDK-TODO How to add optional parameters for configuration, like in the JS-SDK?

## Advanced setup

//SDK-TODO Is it possible to do so in the Python-SDK?