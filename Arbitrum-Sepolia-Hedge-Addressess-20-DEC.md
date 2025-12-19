## 🔑 Core Contracts

| # | Contract Name | Address | Purpose |
|---|---------------|---------|---------|
| 1 | **CoverPool** | `0x11e888B856BB8aBA6936e63e3f78A172EF3808F2` | USDC liquidity pool for backstop coverage |
| 2 | **ProfitDistributor** | `0xdE4B5E4f04ef76d3e6aCcFE4C5fF714a6247d088` | Distributes profits to LPs |
| 3 | **PositionsManager** | `0x4F013A15534D6Ac4FC1530B25a720bC2fe7B139e` | ERC721 NFT manager for options |
| 4 | **ProfitCalculator** | `0xd4d22Ea38AC254448d4562973e0D8D9594c4BCf2` | Calculates option payoffs |
| 5 | **LimitController** | `0x9FdC6AFbb9515Db2FB6b1FB1F3A9E172Bf10D53E` | Controls strategy limits |
| 6 | **OperationalTreasury** | `0xa1758f706A2210076284Fc00AC62AA261894CBcE` | ⭐ **Main contract** - Creates and settles options |

---

## 🪙 Token & Oracle Contracts (Reused)

| Contract Name | Address | Type |
|---------------|---------|------|
| **USDC** | `0x75faf114eafb1BDbe2F0316DF893fd58CE46AA4d` | Settlement Token (6 decimals) |
| **WETH** | `0x980B62Da83eFf3D4576C647993b0c1D7faf17c73` | Underlying Asset (18 decimals) |
| **PriceProviderETH** | `0xd30e2101a97dcbAeBCBC04F14C3f624E67A35165` | Chainlink ETH/USD Oracle (8 decimals) |

---

## ⚙️ Period Configuration (Testing Optimized)

| Parameter | Value | Seconds |
|-----------|-------|---------|
| **maxLockupPeriod** | 7 days | 604,800 |
| **minPeriod** | 1 hour | 3,600 |
| **maxPeriod** | 1 day | 86,400 |
| **exerciseWindowDuration** | 1 day | 86,400 |
| **windowSize** | 1 hour | 3,600 |
| **minimalEpochDuration** | 2 hours | 7,200 |
| **fallbackEpochCloseDuration** | 3 hours | 10,800 |
| **benchmark** | 10,000 USDC | - |
| **strategyLimit** | 20,000 USDC | - |

---

## 📊 ETH Strategies (31 Total)

### 📈 Call Strategies (Bullish)

| Strategy Name | Address | Strike % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_CALL_ETH_100 | `0xB48C5D3486bF4F5Ea7293b8106d3C83c68787097` | 100% (ATM) | `0x62226cF9B0b6e8030FAe7e5C8d1371d103C0DDD9` |
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_CALL_ETH_110 | `0x759903a01BbB3d00D573390C870566F6e99286E4` | 110% (10% OTM) | `0xC5CaDAAF0434Dfb5b34E2bE7a19E17335c46bB20` |
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_CALL_ETH_120 | `0xcC1708c6E2012b82C4c077Ef31084cd028B6Ee43` | 120% (20% OTM) | `0xa454d66eEC60294cc1eb65D0F7c4cAAdF434FC02` |
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_CALL_ETH_130 | `0x24A808528f121ac9775378D61208bD2187aA2237` | 130% (30% OTM) | `0xc4b95C7f85bfAF5F6956cB6c30Da775a3AEFb839` |

### 📉 Put Strategies (Bearish)

| Strategy Name | Address | Strike % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_PUT_ETH_100 | `0x80A6b4124bA00C012d894e8c8791CE633eAaaf00` | 100% (ATM) | `0xF1f33827f06f81F4d1CF91FF097594108B5C7fb2` |
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_PUT_ETH_90 | `0x658355442794c988B467d0678D34650d81abFa4A` | 90% (10% OTM) | `0x1361eFa7A5Fdb9BAD4757fa3A29c5CBC7Fd0f400` |
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_PUT_ETH_80 | `0xb699601a369A938A029Fe26d9BeAC8C3BA0ca7A6` | 80% (20% OTM) | `0x643a3fa00d519D9E3Ef5D96422889cE07d1b4528` |
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_PUT_ETH_70 | `0x3bEfb83de2c768C70cEA2f67B18487dDC2c3e44A` | 70% (30% OTM) | `0x0447eb470d543a6b50Ab90B68b55A782Eea5B94e` |

### 📊 Combination Strategies (High Volatility)

| Strategy Name | Address | Type | Price Calculator |
|---------------|---------|------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_HIGHVOLATILITY_STRADDLE_ETH_100 | `0xca6035571f8E8f75958241114048037831241A50` | ATM Call + Put | `0x95D56DD9C989152c39f0b2B423294a9511c99605` |
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_STRAP_ETH_100 | `0xc6087EB6A786FDAF279B3D4DA0B3cB61f42A43f0` | 2 Calls + 1 Put | `0x19AdFf4f004c118D96C983B848310C3dc27164B4` |
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_STRIP_ETH_100 | `0x88ED0B258BC6b77752E8E16f5401411a667c87Fa` | 1 Call + 2 Puts | `0x8CcB72CCF44343Fd614611727cB831EF1a4Ac027` |

### 📊 Strangle Strategies (High Volatility)

| Strategy Name | Address | Spread % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_HIGHVOLATILITY_STRANGLE_ETH_10 | `0x75Cb6825a2C83560a88588e49A4dD10E8A229040` | 10% | `0x6A89A5fBCAF77143f2930C34e0d2E6A17640D63C` |
| ARBITRUM_SEPOLIA_HEDGE_HIGHVOLATILITY_STRANGLE_ETH_20 | `0x96251364c0ce21aeBA3cd689d8623B0bAcCF527B` | 20% | `0x199E71B4977731171D6411E5F8ab0BCd0fD51c8F` |
| ARBITRUM_SEPOLIA_HEDGE_HIGHVOLATILITY_STRANGLE_ETH_30 | `0xc3F91e8971158D74Bfc07897C1662EBad0C5dAD5` | 30% | `0x8aAb17D54570A804EAF8A6235359deEEb822F730` |

### 📊 Bull Call Spread Strategies

| Strategy Name | Address | Spread % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_CALLSPREAD_ETH_110 | `0x2dbD78d90eC7B124e3a3cD0bbEfE4993A8Eb953B` | 10% | `0x0f93510B7221C2180F2E74298a17446ae9f1aE44` |
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_CALLSPREAD_ETH_120 | `0x700792e9488312Cb6888F29B1d8246E80647e109` | 20% | `0xf4509cC1c08f4Ec6F4509f0E5007db0c682D49B0` |
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_CALLSPREAD_ETH_130 | `0x54e9bd40529882C1A54e01B43d9B3EbEe4b49374` | 30% | `0x10580f712fca2abCEABb8437032D08EB521a0474` |

### 📊 Bear Put Spread Strategies

| Strategy Name | Address | Spread % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_PUTSPREAD_ETH_90 | `0x0AB879b03591853b162EB1e0aA3A98618A9801f1` | 10% | `0x6D350e69DA0972371827f33a7DCD840f13360FfF` |
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_PUTSPREAD_ETH_80 | `0xA7bEeF824aECf5F212857d5f9669D32513F746b0` | 20% | `0xD541A73572dD8bAD1E679b69d2DddEd08912Dd4f` |
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_PUTSPREAD_ETH_70 | `0x298D56B0a282C137C42ac662B21791D30786D049` | 30% | `0x13b49eF04b13c24523CB39664EDf65e11aEd0908` |

### 📊 Bear Call Spread Strategies (Inverse - Low Volatility)

| Strategy Name | Address | Spread % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_CALLSPREAD_ETH_103 | `0x9043e8bA834585c375E9F001F831598a7322C95e` | 10% | `0x83F8F7BcCBDd0083eAC2b8BdD89f460794E51ae9` |
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_CALLSPREAD_ETH_110 | `0x92C86c0bc735892d745D2e3959C8bA4da2aEb446` | 20% | `0xE984986327b0fBA63E0e65361E4937176014a970` |
| ARBITRUM_SEPOLIA_HEDGE_BEARISH_CALLSPREAD_ETH_120 | `0x7F798c3F5159c94c791Dc0Dd616d9998d8A5e537` | 30% | `0xCE52F7DC25897F398eB5Bf65f5366E9ABc7C4784` |

### 📊 Bull Put Spread Strategies (Inverse - Low Volatility)

| Strategy Name | Address | Spread % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_PUTSPREAD_ETH_97 | `0x40175Fc964341047A8409dBB5cB3d1890E1b6806` | 10% | `0xd0cf4Bfa6889BE64EbdFF9F5Dc5C20a4bf264a95` |
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_PUTSPREAD_ETH_90 | `0xEceE9C0bDdc84131127Fdd81F1f91e571de26e49` | 20% | `0x00985F243315D1CBB37aDD6Db044d4c002D99321` |
| ARBITRUM_SEPOLIA_HEDGE_BULLISH_PUTSPREAD_ETH_85 | `0x386ca5Fd46e1C7d9A1b1f75456Fe665C895Abff6` | 30% | `0xaEe44c4af01dbBd50b7bE594157Df0246B1b5E02` |

### 📊 Long Butterfly Strategies (Range-Bound - Low Volatility)

| Strategy Name | Address | Spread % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_LOWVOLATILITY_LONGBUTTERFLY_ETH_115 | `0xAE0D8Ed19Cc00eaFB250cca6F61E23BAE2b0D456` | 10% | `0x54c4043075E7B99Ea4688fF9715D7f7f170db915` |
| ARBITRUM_SEPOLIA_HEDGE_LOWVOLATILITY_LONGBUTTERFLY_ETH_125 | `0xc23f3ea863eF656231c0DB5EEFAa2777076e8a59` | 20% | `0x278c7Db349440ad3bE9D8847aeedCeaD982326fb` |
| ARBITRUM_SEPOLIA_HEDGE_LOWVOLATILITY_LONGBUTTERFLY_ETH_130 | `0x6E063D0Cce1c9A7dbaF44ACAD157B50f204229CE` | 30% | `0x6036F807f264471722c2F44b45Fd70Af32d7B027` |

### 📊 Long Condor Strategies (Range-Bound - Low Volatility)

| Strategy Name | Address | Spread % | Price Calculator |
|---------------|---------|----------|------------------|
| ARBITRUM_SEPOLIA_HEDGE_LOWVOLATILITY_LONGCONDOR_ETH_120 | `0xDe3A0faC3C3DA92E2d48894521800B768d983C62` | 20% | `0x9076Ab42f85b42a609183696f4a5E10f469f15b1` |
| ARBITRUM_SEPOLIA_HEDGE_LOWVOLATILITY_LONGCONDOR_ETH_130 | `0x17bA2acCf956E2499E6c818d989aD54B20171D9F` | 30% | `0x66a693b704c52FaB6090Aa1d993B621acC789E6d` |