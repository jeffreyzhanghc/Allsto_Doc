# Link Integration

Link integration is a quick and straightforward way to incorporate AllsTo's capabilities into your web3 application. It involves opening a link in a new popup window. You can achieve this using JavaScript's `window.open()` function.

## Quick Start

Here is an example of how to open a AllsTo link using `window.open()`. 

```jsx live
function AllsToLink() {
  const link = 'https://t.alls.to/polygon/0x243f22fbd4C375581aaACFCfff5A43793eb8A74d'
  return (
    <button onClick={() => window.open(link, 'Alls.to', 'width=375,height=640')}>
      Open AllsTo Link
    </button>
  )
}
```

Clicking the "Open AllsTo Link" button will open a new window with the specified AllsTo link.

## Link Structure

The AllsTo link structure is constructed as follows: `https://t.alls.to/{chain}/{recipient_address}`. The chain and recipient address are concatenated after the base URL. For testnets, replace the base URL with `https://testnet.t.alls.to/`. See [supported chains and tokens](~/miscellaneous/supported.md).

Here's an example of a AllsTo link for the BNB Testnet:

```jsx live
function AllsToLinkOnTestnet() {
  const link = 'https://testnet.t.alls.to/bnb-testnet/0x00C8B032c76BC8E669ce43b2bA03705Fd52A8edE'
  return (
    <button onClick={() => window.open(link, 'Alls.to', 'width=375,height=640')}>
      Open AllsTo Link on Testnet
    </button>
  )
}
```

## Additional Parameters

### Specify Receiving Token
To specify the receiving token, append `?token={token}` to the end of the link. 

```jsx live
function AllsToLinkWithSpecifiedToken() {
  const link = 'https://t.alls.to/polygon/0x243f22fbd4C375581aaACFCfff5A43793eb8A74d?token=usdt'
  return (
    <button onClick={() => window.open(link, 'Alls.to', 'width=375,height=640')}>
      Open AllsTo Link with Specified Token
    </button>
  )
}
```

```jsx live
function AllsToLinkWithETHSpecified() {
  const link = 'https://t.alls.to/manta/0x243f22fbd4C375581aaACFCfff5A43793eb8A74d?token=eth'
  return (
    <button onClick={() => window.open(link, 'Alls.to', 'width=375,height=640')}>
      Open AllsTo Link with ETH Specified
    </button>
  )
}
```

### Specify Multiple Allowed Tokens
To set multiple allowed tokens, append `?token={t1},{t2}` to the end of the link, with each token separated by a comma. The first option will be set as the default receiving token.

```jsx live
function AllsToLinkWithMultipleAllowedToken() {
  const link = 'https://t.alls.to/bnb/0x243f22fbd4C375581aaACFCfff5A43793eb8A74d?token=busd,usdc'
  return (
    <button onClick={() => window.open(link, 'Alls.to', 'width=375,height=640')}>
      Open AllsTo Link with Multiple Allowed Tokens
    </button>
  )
}
```

In the above example, `busd` will be set as the default receiving token, and the user will also have the option deposit the recipient address with `usdc`.

### Specify the Amount to Transfer
To specify the amount to transfer, append `?amount={amount}` to the end of the link. The amount should be the actual amount of stablecoins, which can be a number with decimals. 

```jsx live
function AllsToLinkWithSpecifiedAmount() {
  const link = 'https://t.alls.to/polygon/0x243f22fbd4C375581aaACFCfff5A43793eb8A74d?amount=4.99'
  return (
    <button onClick={() => window.open(link, 'Alls.to', 'width=375,height=640')}>
      Open AllsTo Link with Specified Amount
    </button>
  )
}
```

In the above example, the link will ask the user to transfer stablecoins with an amount of 4.99, which typically values $4.99.

It's worth noting that you can combine the use of `token` and `amount` parameters together to further customize the link. For example, appending `?token=usdt&amount=4.99` to the end of the link will specify both the token type and amount in the transfer request.
