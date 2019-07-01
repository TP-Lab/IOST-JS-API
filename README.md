## IOST Dapp

- 更多可用的钱包相关特性 请查看 https://github.com/TP-Lab/tp-js-sdk
- More API about TokenPocket, please check https://github.com/TP-Lab/tp-js-sdk


``` javascript

import IOST from 'iost'

IWalletJS.enable().then((account) => {
    if(!account) return; // not login

    const iost = IWalletJS.newIOST(IOST)

    //transfer
    const tx = iost.transfer('iost', account, "testiost1", "1.000", "this is memo")
    
    iost.signAndSend(tx)
    .on('pending', (trx) => {
      console.log(trx, 'trx')
    })
    .on('success', (result) => {
      console.log(result, 'result')
    })
    .on('failed', (failed) => {
      console.log(failed, 'failed')
    })

    const ctx = iost.callABI('contractAddress', "hello", ['args']);

    iost.signAndSend(ctx)
    ...
})

``` 
