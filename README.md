# Product Registry Lookup v4.0

A lightweight, browser-based tool for verifying product authenticity against a smart contract deployed on the **Polygon blockchain**. No backend required — all validation is done directly on-chain via a public RPC endpoint.

---

## 🔍 Overview

This single-page application allows users to check whether a product ID is registered and valid by querying a Solidity smart contract on the Polygon network. It is designed to be simple, portable, and tamper-resistant — leveraging blockchain immutability for product authentication.

---

## ✨ Features

- **On-chain validation** — queries a deployed smart contract directly from the browser
- **Manual lookup** — enter any Product ID via the input field
- **URL-based auto-check** — pass a `?validate=<productId>` query parameter to trigger an automatic check on page load
- **Clear visual feedback** — green ✅ for valid products, red ❌ for unregistered ones
- **Zero dependencies to install** — uses ethers.js via CDN

---

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Edge, Safari)
- No Node.js, npm, or build tools required

### Usage

1. Clone or download the project files.
2. Open `index.html` directly in your browser.
3. Enter a Product ID in the input field and click **Check Product**.

### URL Parameter (Auto-Validate)

You can also trigger a validation automatically by appending a query string to the URL:

```
index.html?validate=12345
```

The page will load and immediately check product ID `12345` without any manual input.

---

## 🔗 Smart Contract Details

| Property         | Value                                        |
|------------------|----------------------------------------------|
| **Network**      | Polygon (Matic) Mainnet                      |
| **Contract Address** | `0xd0Ce7A438998460C74262E3524481fD7744a2462` |
| **RPC Provider** | QuikNode (Polygon)                           |
| **ABI Function** | `validateProduct(uint256 _productId) → bool` |

The contract exposes a single read-only function:

```solidity
function validateProduct(uint256 _productId) public view returns (bool)
```

Returns `true` if the product is registered, `false` otherwise.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| HTML/CSS/JS | Frontend UI |
| [Ethers.js v6.7.0](https://docs.ethers.org/) | Blockchain interaction |
| Polygon Network | Smart contract hosting |
| QuikNode RPC | Blockchain node access |

---

## 📁 Project Structure

```
project/
└── index.html      # Single-file application (UI + logic)
```

---

## ⚠️ Notes

- The RPC URL is embedded in the frontend code. For production use, consider proxying it through a backend to avoid exposing your endpoint publicly.
- Product IDs must be valid `uint256` integers as expected by the smart contract.
- Ensure you are connected to the internet, as the app requires live access to the Polygon RPC node.

---

## 📄 License

This project is open source. Feel free to modify and distribute it as needed.
