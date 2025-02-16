﻿# ✨ Welcome to Unofficial Chapa NodeJS SDK! 



## 🔧 Features

With the Chapa Node.js SDK, you can seamlessly integrate payment and transaction functionalities into your application. Here's a quick overview of its capabilities:






Full TypeScript Support: Write robust and type-safe code.
Here's what Chapa SDK can do for you:

- ✨ **Initialize Transactions:** Start a payment transaction effortlessly.
- ✨ **Verify Payments:** Confirm the success of a transaction.
- ✨ **Split Payments:** Allocate payments across multiple subaccounts with precision.
- ✨ **List Banks:** Access detailed information on supported banks.
- ✨ **Create Subaccounts:** Set up subaccounts for payment splitting.
- ✨ **Retrieve All Transactions:** Fetch a comprehensive list of all transactions.
- ✨ **Transaction Logs:** View detailed event logs for specific transactions.
- ✨ **Send Transfers:** Transfer funds to individual bank accounts.
- ✨ **Bulk Transfers:** Initiate multiple fund transfers at once.
- ✨ **Retrieve All Transfers:** Retrieve a list of all transfers made.
- ✨ **Verify Transfers:** Confirm the status of a transfer.
- ✨ **Authorize Direct Charges:**  Enable and manage direct charge authorization.
- ✨ **Generate Transaction References:** Create unique and customizable transaction references with ease.
- ✨ **Direct Charges:** Handle direct charges seamlessly.
- ✨ **Full TypeScript Support**

---

## 🔍 Installation

Install Chapa SDK with your preferred package manager:

### 🔄 NPM
```bash
npm install chapa-nodejs
```

### ✨ Yarn
```bash
yarn add chapa-nodejs
```

### ☕ Pnpm
```bash
pnpm add chapa-nodejs
```

---

## 🌟 Getting Started

Once installed, you can import Chapa SDK and start building your payment integrations. Let’s make this super easy for you! 🚀

### Configuration

Make sure to load your secret key from an environment variable. Here's how:

```typescript
import { Chapa } from 'chapa-nodejs';

const chapa = new Chapa({
  secretKey: 'your-chapa-secret-key',
});
```

---

### ✨ Generate Transaction Reference

This utility method generates a customizable, random alphanumeric transaction reference:

```typescript
const tx_ref = await chapa.genTxRef(); // e.g., TX-JHBUVLM7HYMSWDA

// Or with custom options:
const tx_ref = await chapa.genTxRef({
  removePrefix: false, // defaults to `false`
  prefix: 'TX', // defaults to `TX`
  size: 20, // defaults to `15`
});
```

---

### 💳 Initialize Transaction

Ready to accept payments? Use the `initialize` method for web payments or `mobileInitialize` for mobile payments.

#### Web Payment

```typescript
const tx_ref = await chapa.genTxRef();

const response = await chapa.initialize({
  first_name: 'John',
  last_name: 'Doe',
  email: 'john@gmail.com',
  phone_number: '0911121314',
  currency: 'ETB',
  amount: '200',
  tx_ref: tx_ref,
  callback_url: 'https://example.com/',
  return_url: 'https://example.com/',
  customization: {
    title: 'Test Title',
    description: 'Test Description',
  },
});
```

#### Mobile Payment

```typescript
const tx_ref = await chapa.genTxRef();

const response = await chapa.mobileInitialize({
  first_name: 'John',
  last_name: 'Doe',
  email: 'john@gmail.com',
  phone_number: '0911121314',
  currency: 'ETB',
  amount: '200',
  tx_ref: tx_ref,
  callback_url: 'https://example.com/',
  return_url: 'https://example.com/',
  customization: {
    title: 'Test Title',
    description: 'Test Description',
  },
});
```

---

### 📋 Verify Payment

To confirm payment status, call the `verify` method with your transaction reference:

```typescript
const response = await chapa.verify({
  tx_ref: 'TX-JHBUVLM7HYMSWDA',
});
```

---

### 🏦 List Banks

Retrieve all supported banks effortlessly:

```typescript
const response = await chapa.getBanks();
```

---

### 🏩 Create Subaccount

Simplify payment splitting by creating subaccounts:

```typescript
const response = await chapa.createSubaccount({
  business_name: 'Test Business',
  account_name: 'John Doe',
  bank_code: '80a510ea-7497-4499-8b49-ac13a3ab7d07',
  account_number: '0123456789',
  split_type: SplitType.PERCENTAGE,
  split_value: 0.02,
});
```

---

### 📈 Split Payment

Easily split payments between multiple accounts:

```typescript
const tx_ref = await chapa.genTxRef();

const response = chapa.initialize({
  first_name: 'John',
  last_name: 'Doe',
  email: 'john@gmail.com',
  phone_number: '0911121314',
  currency: 'ETB',
  amount: '200',
  tx_ref: tx_ref,
  callback_url: 'https://example.com/',
  return_url: 'https://example.com/',
  customization: {
    title: 'Test Title',
    description: 'Test Description',
  },
  subaccounts: [
    {
      id: '80a510ea-7497-4499-8b49-ac13a3ab7d07',
    },
  ],
});
```

---

## ✨ Keep in Touch

Hi, I’m Solomon Getnet! If you have any questions or need help with Chapa SDK, feel free to reach out:

- 🎨 **Author**: Solomon getnet
- 🔎 **Github**: [Solaget](https://github.com/solaget)  
---

✨ Happy Coding! ✨

