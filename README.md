# shopyverse-dapp

Shopyverse Ton dApp  using [OpenMask TON Wallet Plugin]


## API

TON Wallet Plugin injects in page `window.ton` object.

Plugin doesn't inject [TonWeb](https://github.com/toncenter/tonweb) library, but you can include it by yourself; In the future you will be able to use `ton` as provider: `new TonWeb(window.ton)`

### Detecting TON Wallet Plugin

`ton.isTonWallet`

### Requests to Plugin

`ton.send(method: string, params?: Array<any>): Promise<any>;` - The way to send requests to the plugin. 

Currently there are 3 methods:

`ton.send('ton_requestAccounts'): Promise<string[]>` - get user wallet address.

`ton.send('ton_sendTransaction', {value: string, to: string, data: string})` - send TON coins.

Where `value` - nanotons to send,
`to` - destination address,
`data` - additional data (comment)

`ton.send('ton_getBalance'): Promise<string>` - get user current wallet balance in nanotons.


### Plugin Events

`ton.on(eventName: string, listener: (result: any) => void)` - The way to add event listener to the plugin.

Currently there is 1 event:

`ton.on('accountsChanged', listener: (accounts: Array<string>) => void)` - emitted when user changed account.
