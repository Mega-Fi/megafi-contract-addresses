# 🧪 Arbitrum Sepolia Test Deployment

## 🔑 Core Contracts

| # | Contract Name | Address | Purpose |
|---|---------------|---------|---------|
| 1 | **CoverPool** | `0x1C786D28341340e6A9b47ddB8c3e20E719562BB5` | USDC liquidity pool for backstop coverage |
| 2 | **ProfitDistributor** | `0xFF9031382D9cdd44A95FC6e5EbE74BF2C3591069` | Distributes profits to LPs |
| 3 | **PositionsManager** | `0x82e01f039Caa5e423810B48B2b0fCA98Bb5e230e` | ERC721 NFT manager for options |
| 4 | **ProfitCalculator** | `0xDb7D577F1345AD74B125501F4B68240F44ed7e60` | Calculates option payoffs |
| 5 | **LimitController** | `0x06d275553219068F4186a71B92200FeA2Ec17Ed5` | Controls strategy limits |
| 6 | **OperationalTreasury** | `0xdE19737db2325DD2aA072713aEaa7db4F4b23009` | ⭐ **Main contract** - Creates and settles options |

---

## 🔄 Updated Price Calculators (FlexiblePolynomialPriceCalculator)

**Note**: These are the new FlexiblePolynomialPriceCalculator contracts that support 1-hour minimum periods. All 32 CALL and PUT strategies have been connected to these new calculators.

| Price Calculator | New Address | Old Address | Type | Period Limits |
|------------------|-------------|-------------|------|---------------|
| **FlexiblePriceCalculator_CALL_100_ETH** | `0x62226cF9B0b6e8030FAe7e5C8d1371d103C0DDD9` | `0xA59180C506A9C89DB47E49A332d2363F8288c1Af` | CALL 100% | 1 hour - 1 day |
| **FlexiblePriceCalculator_CALL_110_ETH** | `0xC5CaDAAF0434Dfb5b34E2bE7a19E17335c46bB20` | `0x903E122119F53F87c8017B23EEC2C3496A9F05c6` | CALL 110% | 1 hour - 1 day |
| **FlexiblePriceCalculator_CALL_120_ETH** | `0xa454d66eEC60294cc1eb65D0F7c4cAAdF434FC02` | `0xb59476b53351Cd1b26ead70835E5ED7B8929b409` | CALL 120% | 1 hour - 1 day |
| **FlexiblePriceCalculator_CALL_130_ETH** | `0xc4b95C7f85bfAF5F6956cB6c30Da775a3AEFb839` | `0xFfBae80a2D49BeF876509fad228cC6DAC582934E` | CALL 130% | 1 hour - 1 day |
| **FlexiblePriceCalculator_PUT_100_ETH** | `0xF1f33827f06f81F4d1CF91FF097594108B5C7fb2` | `0xDCCd37e49123071fcb0396299Bbe8544d0FB7b43` | PUT 100% | 1 hour - 1 day |
| **FlexiblePriceCalculator_PUT_90_ETH** | `0x1361eFa7A5Fdb9BAD4757fa3A29c5CBC7Fd0f400` | `0x7aA123BE6d53d8A7431a45AFfEB29C50896847d8` | PUT 90% | 1 hour - 1 day |
| **FlexiblePriceCalculator_PUT_80_ETH** | `0x643a3fa00d519D9E3Ef5D96422889cE07d1b4528` | `0x34434b4d4e2b69241562e1fd16968acA05e921c0` | PUT 80% | 1 hour - 1 day |
| **FlexiblePriceCalculator_PUT_70_ETH** | `0x0447eb470d543a6b50Ab90B68b55A782Eea5B94e` | `0x626fBdc6E45414b7Ca0f2013b705f0e25040a14D` | PUT 70% | 1 hour - 1 day |

### ⚠️ Legacy Price Calculators (Deprecated)

The following old PriceCalculator contracts are no longer in use. All 32 CALL and PUT strategies have been migrated to the new FlexiblePolynomialPriceCalculator contracts above.

---

## 🪙 Token & Oracle Contracts

| Contract Name | Address | Type |
|---------------|---------|------|
| **USDC** | `0x75faf114eafb1BDbe2F0316DF893fd58CE46AA4d` | Settlement Token |
| **WETH** | `0x980B62Da83eFf3D4576C647993b0c1D7faf17c73` | Underlying Asset |
| **PriceProviderETH** | `0xd30e2101a97dcbAeBCBC04F14C3f624E67A35165` | Chainlink ETH/USD Oracle |

---

## ⚙️ Period Configuration (Testing Optimized)

All period values have been configured for fast testing cycles:

| Parameter | Value | Seconds | Setter Function |
|-----------|-------|---------|----------------|
| **maxLockupPeriod** | 7 days | 604,800 | `setMaxLockupPeriod()` |
| **minPeriod** | 1 hour | 3,600 | `setPeriodLimits()` |
| **maxPeriod** | 1 day | 86,400 | `setPeriodLimits()` |
| **exerciseWindowDuration** | 2 hours | 7,200 | `setExerciseWindowDuration()` |
| **windowSize** | 1 hour | 3,600 | `setWindowSize()` |
| **MINIMAL_EPOCH_DURATION** | 2 hours | 7,200 | `setEpochDuration()` |
| **fallbackEpochCloseDuration** | 3 hours | 10,800 | `setFallbackEpochCloseDuration()` |

**All variables are now mutable and can be changed via setter functions for testing flexibility.**

---

## 📊 ETH CALL Strategies

### CALL 100% (ATM - At The Money)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_CALL_100_ETH_1 | `0x4aA2dB24AdC9c2ad0d5C10A96121093Dee810Ea5` | FlexiblePriceCalculator_CALL_100_ETH | `0x62226cF9B0b6e8030FAe7e5C8d1371d103C0DDD9` |
| HegicStrategy_CALL_100_ETH_2 | `0x79d07802E6C2f7AC48153248547829c71Ac43550` | FlexiblePriceCalculator_CALL_100_ETH | `0x62226cF9B0b6e8030FAe7e5C8d1371d103C0DDD9` |
| HegicStrategy_CALL_100_ETH_3 | `0x8e7CBEdeFa8Af10f223Cc3e7F962C6Dad807373B` | FlexiblePriceCalculator_CALL_100_ETH | `0x62226cF9B0b6e8030FAe7e5C8d1371d103C0DDD9` |
| HegicStrategy_CALL_100_ETH_4 | `0xF3385D57fA2558964c7c279C91eA6FeF9730dcD9` | FlexiblePriceCalculator_CALL_100_ETH | `0x62226cF9B0b6e8030FAe7e5C8d1371d103C0DDD9` |

### CALL 110% (10% OTM - Out of The Money)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_CALL_110_ETH_1 | `0x8D8421b549FC8bf29c257A192e072Db8881a181D` | FlexiblePriceCalculator_CALL_110_ETH | `0xC5CaDAAF0434Dfb5b34E2bE7a19E17335c46bB20` |
| HegicStrategy_CALL_110_ETH_2 | `0x464833AcfE300A3F48aE2c8c9072b033e11257d6` | FlexiblePriceCalculator_CALL_110_ETH | `0xC5CaDAAF0434Dfb5b34E2bE7a19E17335c46bB20` |
| HegicStrategy_CALL_110_ETH_3 | `0x8CE876f237c63726125E959580c5b5BDe748d72a` | FlexiblePriceCalculator_CALL_110_ETH | `0xC5CaDAAF0434Dfb5b34E2bE7a19E17335c46bB20` |
| HegicStrategy_CALL_110_ETH_4 | `0x277877cDba755EFCEfFC2a47A9A4a5294331BF58` | FlexiblePriceCalculator_CALL_110_ETH | `0xC5CaDAAF0434Dfb5b34E2bE7a19E17335c46bB20` |

### CALL 120% (20% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_CALL_120_ETH_1 | `0x3c8a1C67d81385A4c66966900b9a8f47Ed5ed29B` | FlexiblePriceCalculator_CALL_120_ETH | `0xa454d66eEC60294cc1eb65D0F7c4cAAdF434FC02` |
| HegicStrategy_CALL_120_ETH_2 | `0x58eB94dA4e631d9Ad18a8cD446894D8Ec0dd4bbb` | FlexiblePriceCalculator_CALL_120_ETH | `0xa454d66eEC60294cc1eb65D0F7c4cAAdF434FC02` |
| HegicStrategy_CALL_120_ETH_3 | `0x1b9493A0a6cfb80D6b7Fb958A695198399620Eb9` | FlexiblePriceCalculator_CALL_120_ETH | `0xa454d66eEC60294cc1eb65D0F7c4cAAdF434FC02` |
| HegicStrategy_CALL_120_ETH_4 | `0x7925804d0bE796d7a10627527Fd4D04ebbe2ED4E` | FlexiblePriceCalculator_CALL_120_ETH | `0xa454d66eEC60294cc1eb65D0F7c4cAAdF434FC02` |

### CALL 130% (30% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_CALL_130_ETH_1 | `0x22ea8743fC5fA78Fc95cb0F9aF53B72195220d11` | FlexiblePriceCalculator_CALL_130_ETH | `0xc4b95C7f85bfAF5F6956cB6c30Da775a3AEFb839` |
| HegicStrategy_CALL_130_ETH_2 | `0x3D48c7f0F7b781ef5633945c6Dc93FB7F24C7d6B` | FlexiblePriceCalculator_CALL_130_ETH | `0xc4b95C7f85bfAF5F6956cB6c30Da775a3AEFb839` |
| HegicStrategy_CALL_130_ETH_3 | `0xe59eFe044c48a56D00f12BA449aBf0C1cB394946` | FlexiblePriceCalculator_CALL_130_ETH | `0xc4b95C7f85bfAF5F6956cB6c30Da775a3AEFb839` |
| HegicStrategy_CALL_130_ETH_4 | `0x0281396746A4375Eb547C63210985Cdf58df8175` | FlexiblePriceCalculator_CALL_130_ETH | `0xc4b95C7f85bfAF5F6956cB6c30Da775a3AEFb839` |

---

## 📉 ETH PUT Strategies

### PUT 100% (ATM - At The Money)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_PUT_100_ETH_1 | `0x71737F6bE4095bB11e17EA30D90952150d48CEf2` | FlexiblePriceCalculator_PUT_100_ETH | `0xF1f33827f06f81F4d1CF91FF097594108B5C7fb2` |
| HegicStrategy_PUT_100_ETH_2 | `0x0dc0271b96588AEB478FE16Ae0df0F91944F7041` | FlexiblePriceCalculator_PUT_100_ETH | `0xF1f33827f06f81F4d1CF91FF097594108B5C7fb2` |
| HegicStrategy_PUT_100_ETH_3 | `0xC88426abC1a8962d4d33FBEc8D4b593af3d11cC3` | FlexiblePriceCalculator_PUT_100_ETH | `0xF1f33827f06f81F4d1CF91FF097594108B5C7fb2` |
| HegicStrategy_PUT_100_ETH_4 | `0x59D2Eed270742b48971DF08d65aec9327c41a20B` | FlexiblePriceCalculator_PUT_100_ETH | `0xF1f33827f06f81F4d1CF91FF097594108B5C7fb2` |

### PUT 90% (10% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_PUT_90_ETH_1 | `0x506d76E67Cc29519917F741c5709DA184E0E3d20` | FlexiblePriceCalculator_PUT_90_ETH | `0x1361eFa7A5Fdb9BAD4757fa3A29c5CBC7Fd0f400` |
| HegicStrategy_PUT_90_ETH_2 | `0x1304E97Ab92d83F256e3623aC4E27aeB364bC44A` | FlexiblePriceCalculator_PUT_90_ETH | `0x1361eFa7A5Fdb9BAD4757fa3A29c5CBC7Fd0f400` |
| HegicStrategy_PUT_90_ETH_3 | `0x90cA27468527C5044f4d05DB051206793AeDcdeb` | FlexiblePriceCalculator_PUT_90_ETH | `0x1361eFa7A5Fdb9BAD4757fa3A29c5CBC7Fd0f400` |
| HegicStrategy_PUT_90_ETH_4 | `0x0456530b44a80DC88D5410A1B627F8FA4B8530Ac` | FlexiblePriceCalculator_PUT_90_ETH | `0x1361eFa7A5Fdb9BAD4757fa3A29c5CBC7Fd0f400` |

### PUT 80% (20% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_PUT_80_ETH_1 | `0x4bF787797843796a988BDd857Ed20769841f4D96` | FlexiblePriceCalculator_PUT_80_ETH | `0x643a3fa00d519D9E3Ef5D96422889cE07d1b4528` |
| HegicStrategy_PUT_80_ETH_2 | `0x7b396964cc333CC0EBC37Ff271070C93E421e08D` | FlexiblePriceCalculator_PUT_80_ETH | `0x643a3fa00d519D9E3Ef5D96422889cE07d1b4528` |
| HegicStrategy_PUT_80_ETH_3 | `0x169c84f4Fcfd61894B1E9ccAe1a4F668cB911914` | FlexiblePriceCalculator_PUT_80_ETH | `0x643a3fa00d519D9E3Ef5D96422889cE07d1b4528` |
| HegicStrategy_PUT_80_ETH_4 | `0xedd861Ee1aC915bD89286EF1cfcE9DFeCF1E8499` | FlexiblePriceCalculator_PUT_80_ETH | `0x643a3fa00d519D9E3Ef5D96422889cE07d1b4528` |

### PUT 70% (30% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_PUT_70_ETH_1 | `0xA35047FE5178c6D2d4B6465937d02DF46151621C` | FlexiblePriceCalculator_PUT_70_ETH | `0x0447eb470d543a6b50Ab90B68b55A782Eea5B94e` |
| HegicStrategy_PUT_70_ETH_2 | `0xCE4A8FC81bd300BD0719EACBBE946962fD79FDF3` | FlexiblePriceCalculator_PUT_70_ETH | `0x0447eb470d543a6b50Ab90B68b55A782Eea5B94e` |
| HegicStrategy_PUT_70_ETH_3 | `0x16b7211E02D094C214414E5227655DA873443670` | FlexiblePriceCalculator_PUT_70_ETH | `0x0447eb470d543a6b50Ab90B68b55A782Eea5B94e` |
| HegicStrategy_PUT_70_ETH_4 | `0x2A1A1fBDc95678E0fC2e174D915f18284A757F77` | FlexiblePriceCalculator_PUT_70_ETH | `0x0447eb470d543a6b50Ab90B68b55A782Eea5B94e` |

---

## 📈 ETH SPREAD CALL Strategies

### SPREAD CALL 10% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_SPREAD_CALL_10_ETH_1 | `0x3FE02E806a9926DE0C8a14de9E3a333cb41D09aa` | PriceCalculator_SPREAD_CALL_10_ETH | `0x0f93510B7221C2180F2E74298a17446ae9f1aE44` |
| HegicStrategy_SPREAD_CALL_10_ETH_2 | `0x1736c52F2969C9aFE993F75661DAcFA3a28b81ae` | PriceCalculator_SPREAD_CALL_10_ETH | `0x0f93510B7221C2180F2E74298a17446ae9f1aE44` |
| HegicStrategy_SPREAD_CALL_10_ETH_3 | `0xe1b625a47a57eA5CC07DAd4FA2EF1B9C65860Af5` | PriceCalculator_SPREAD_CALL_10_ETH | `0x0f93510B7221C2180F2E74298a17446ae9f1aE44` |
| HegicStrategy_SPREAD_CALL_10_ETH_4 | `0xA927e3b93383D49E5cFF6EC0268d19CB1b0b156d` | PriceCalculator_SPREAD_CALL_10_ETH | `0x0f93510B7221C2180F2E74298a17446ae9f1aE44` |

### SPREAD CALL 20% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_SPREAD_CALL_20_ETH_1 | `0x26c45f1B51028EBeFC205e9f508F3F9a42537e34` | PriceCalculator_SPREAD_CALL_20_ETH | `0xf4509cC1c08f4Ec6F4509f0E5007db0c682D49B0` |
| HegicStrategy_SPREAD_CALL_20_ETH_2 | `0xb921eE7f8Ba0eDf875a5a52DE0f4A0aB2940e3cB` | PriceCalculator_SPREAD_CALL_20_ETH | `0xf4509cC1c08f4Ec6F4509f0E5007db0c682D49B0` |
| HegicStrategy_SPREAD_CALL_20_ETH_3 | `0x3E79c59F8ad7710355664d08a4F2E001e7be45B4` | PriceCalculator_SPREAD_CALL_20_ETH | `0xf4509cC1c08f4Ec6F4509f0E5007db0c682D49B0` |
| HegicStrategy_SPREAD_CALL_20_ETH_4 | `0xf2212eaDD017e7e74a10d764F946c9e5554044eE` | PriceCalculator_SPREAD_CALL_20_ETH | `0xf4509cC1c08f4Ec6F4509f0E5007db0c682D49B0` |

### SPREAD CALL 30% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_SPREAD_CALL_30_ETH_1 | `0x4fF41dC45E37ecAFa627D31F726B10a9EdF1B211` | PriceCalculator_SPREAD_CALL_30_ETH | `0x10580f712fca2abCEABb8437032D08EB521a0474` |
| HegicStrategy_SPREAD_CALL_30_ETH_2 | `0xCFA17be9CdB0e05a43a4ED5a6F3CAbf8a42FB737` | PriceCalculator_SPREAD_CALL_30_ETH | `0x10580f712fca2abCEABb8437032D08EB521a0474` |
| HegicStrategy_SPREAD_CALL_30_ETH_3 | `0x2E78AAE8b75D5D43cbECFAC332977E9e799fbFcB` | PriceCalculator_SPREAD_CALL_30_ETH | `0x10580f712fca2abCEABb8437032D08EB521a0474` |
| HegicStrategy_SPREAD_CALL_30_ETH_4 | `0xec90D0505ACd7DA92FDA3dB15AC6b4370D2406c8` | PriceCalculator_SPREAD_CALL_30_ETH | `0x10580f712fca2abCEABb8437032D08EB521a0474` |

---

## 📉 ETH SPREAD PUT Strategies

### SPREAD PUT 10% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_SPREAD_PUT_10_ETH_1 | `0xa9f26EBFda3f934100698020e0cd4a67AE8eD6D7` | PriceCalculator_SPREAD_PUT_10_ETH | `0x6D350e69DA0972371827f33a7DCD840f13360FfF` |
| HegicStrategy_SPREAD_PUT_10_ETH_2 | `0x9409E3a7ea945b2D0C6A2ffBEf3222ce056F6d07` | PriceCalculator_SPREAD_PUT_10_ETH | `0x6D350e69DA0972371827f33a7DCD840f13360FfF` |
| HegicStrategy_SPREAD_PUT_10_ETH_3 | `0x35724560728E2895480E36A56e53139C98a3F55D` | PriceCalculator_SPREAD_PUT_10_ETH | `0x6D350e69DA0972371827f33a7DCD840f13360FfF` |
| HegicStrategy_SPREAD_PUT_10_ETH_4 | `0x704a6F9be75D9c35615F5681FBCE0068c342d919` | PriceCalculator_SPREAD_PUT_10_ETH | `0x6D350e69DA0972371827f33a7DCD840f13360FfF` |

### SPREAD PUT 20% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_SPREAD_PUT_20_ETH_1 | `0xEd3dE112dF3C95CBF1d3BCFB5125F8b95673511b` | PriceCalculator_SPREAD_PUT_20_ETH | `0xD541A73572dD8bAD1E679b69d2DddEd08912Dd4f` |
| HegicStrategy_SPREAD_PUT_20_ETH_2 | `0xdadAe1052687bC8C6E85d4F9918C304f20beBa1a` | PriceCalculator_SPREAD_PUT_20_ETH | `0xD541A73572dD8bAD1E679b69d2DddEd08912Dd4f` |
| HegicStrategy_SPREAD_PUT_20_ETH_3 | `0x28eE69C20069959D0b92F66FdA8F773422f36cb9` | PriceCalculator_SPREAD_PUT_20_ETH | `0xD541A73572dD8bAD1E679b69d2DddEd08912Dd4f` |
| HegicStrategy_SPREAD_PUT_20_ETH_4 | `0x5B0b7D98799344822aC6a923456817D7a1B442Fb` | PriceCalculator_SPREAD_PUT_20_ETH | `0xD541A73572dD8bAD1E679b69d2DddEd08912Dd4f` |

### SPREAD PUT 30% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_SPREAD_PUT_30_ETH_1 | `0x48B542B2383A937E817fd5e89857d43046155e2f` | PriceCalculator_SPREAD_PUT_30_ETH | `0x13b49eF04b13c24523CB39664EDf65e11aEd0908` |
| HegicStrategy_SPREAD_PUT_30_ETH_2 | `0x3DA57E9f047e4bD5f3BF210f8D986992bAb4BEc3` | PriceCalculator_SPREAD_PUT_30_ETH | `0x13b49eF04b13c24523CB39664EDf65e11aEd0908` |
| HegicStrategy_SPREAD_PUT_30_ETH_3 | `0x9A548a619Dac5576ba6071dd4774984081C30EF4` | PriceCalculator_SPREAD_PUT_30_ETH | `0x13b49eF04b13c24523CB39664EDf65e11aEd0908` |
| HegicStrategy_SPREAD_PUT_30_ETH_4 | `0x5BF3c98753c00E632009A63926a894D712079302` | PriceCalculator_SPREAD_PUT_30_ETH | `0x13b49eF04b13c24523CB39664EDf65e11aEd0908` |

---

## 🔀 ETH STRADDLE Strategies

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_STRADDLE_ETH_1 | `0xecb3116bCcb9e308f523f240D4bE9a0e623D788A` | PriceCalculator_STRADDLE_ETH | `0x95D56DD9C989152c39f0b2B423294a9511c99605` |
| HegicStrategy_STRADDLE_ETH_2 | `0x296C398f03A46b0eEBd500Dec25FE6E89BF81e29` | PriceCalculator_STRADDLE_ETH | `0x95D56DD9C989152c39f0b2B423294a9511c99605` |
| HegicStrategy_STRADDLE_ETH_3 | `0x4E6305971d81d0464CcD21f40D1632b6d15a700c` | PriceCalculator_STRADDLE_ETH | `0x95D56DD9C989152c39f0b2B423294a9511c99605` |
| HegicStrategy_STRADDLE_ETH_4 | `0x92e9D2140515E6F2cB83b63C9e7b9ED5B190a82d` | PriceCalculator_STRADDLE_ETH | `0x95D56DD9C989152c39f0b2B423294a9511c99605` |

---

## 🔀 ETH STRANGLE Strategies

### STRANGLE 10% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_STRANGLE_10_ETH_1 | `0xb17DC9e9D3d2Aeea409B22a788Db60D567776e2D` | PriceCalculator_STRANGLE_10_ETH | `0x6A89A5fBCAF77143f2930C34e0d2E6A17640D63C` |
| HegicStrategy_STRANGLE_10_ETH_2 | `0x27Ff99b24Cf261Ef9feC0D462335F0E7168d0871` | PriceCalculator_STRANGLE_10_ETH | `0x6A89A5fBCAF77143f2930C34e0d2E6A17640D63C` |
| HegicStrategy_STRANGLE_10_ETH_3 | `0x97aa7BAc49b4673c6f632A23AF96826ebDD12020` | PriceCalculator_STRANGLE_10_ETH | `0x6A89A5fBCAF77143f2930C34e0d2E6A17640D63C` |
| HegicStrategy_STRANGLE_10_ETH_4 | `0xBd682C0bE72945E4630039774A75E3D42a5200A5` | PriceCalculator_STRANGLE_10_ETH | `0x6A89A5fBCAF77143f2930C34e0d2E6A17640D63C` |

### STRANGLE 20% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_STRANGLE_20_ETH_1 | `0x9104eB66Ae1CD025cC9B745E7EDa046B26278D5e` | PriceCalculator_STRANGLE_20_ETH | `0x199E71B4977731171D6411E5F8ab0BCd0fD51c8F` |
| HegicStrategy_STRANGLE_20_ETH_2 | `0x473d605938E1f9bee005fC6F8DB4Cddb52Df08E4` | PriceCalculator_STRANGLE_20_ETH | `0x199E71B4977731171D6411E5F8ab0BCd0fD51c8F` |
| HegicStrategy_STRANGLE_20_ETH_3 | `0xA72D08601fC8D8582652b053c0e8174f1f9fB098` | PriceCalculator_STRANGLE_20_ETH | `0x199E71B4977731171D6411E5F8ab0BCd0fD51c8F` |
| HegicStrategy_STRANGLE_20_ETH_4 | `0xA565ed6ca5Cc0A020670fC77d80C52737e83655D` | PriceCalculator_STRANGLE_20_ETH | `0x199E71B4977731171D6411E5F8ab0BCd0fD51c8F` |

### STRANGLE 30% Spread

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_STRANGLE_30_ETH_1 | `0x41faE878e1f8B6818E990e06E31303cA2AfA1215` | PriceCalculator_STRANGLE_30_ETH | `0x8aAb17D54570A804EAF8A6235359deEEb822F730` |
| HegicStrategy_STRANGLE_30_ETH_2 | `0xc8a74e9B3D2707B661Ef61fa7e37ff3A0948C70e` | PriceCalculator_STRANGLE_30_ETH | `0x8aAb17D54570A804EAF8A6235359deEEb822F730` |
| HegicStrategy_STRANGLE_30_ETH_3 | `0x912CC3aA98EEE32Ef9e6D9a88678fc5a0ce7bf00` | PriceCalculator_STRANGLE_30_ETH | `0x8aAb17D54570A804EAF8A6235359deEEb822F730` |
| HegicStrategy_STRANGLE_30_ETH_4 | `0x1aAc7eD7b9c7D6E022E3c86fAB814815e3006B27` | PriceCalculator_STRANGLE_30_ETH | `0x8aAb17D54570A804EAF8A6235359deEEb822F730` |

---

## 🔀 ETH STRAP Strategies

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_STRAP_ETH_1 | `0x74369Bd38d218c526519Ed4f2597bd538C9408Ab` | PriceCalculator_STRAP_ETH | `0x19AdFf4f004c118D96C983B848310C3dc27164B4` |
| HegicStrategy_STRAP_ETH_2 | `0x56be07120039cA02bA489416059E0645B4F9B1aE` | PriceCalculator_STRAP_ETH | `0x19AdFf4f004c118D96C983B848310C3dc27164B4` |
| HegicStrategy_STRAP_ETH_3 | `0x536548B9545af072328a1DE1077e6aD45da1C7C1` | PriceCalculator_STRAP_ETH | `0x19AdFf4f004c118D96C983B848310C3dc27164B4` |
| HegicStrategy_STRAP_ETH_4 | `0x17C353cC9156896cAC1254EbD85FffCAA61A037E` | PriceCalculator_STRAP_ETH | `0x19AdFf4f004c118D96C983B848310C3dc27164B4` |

---

## 🔀 ETH STRIP Strategies

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_STRIP_ETH_1 | `0x5C72EcA25bA719BA70432F2E8F2190427c3ef228` | PriceCalculator_STRIP_ETH | `0x8CcB72CCF44343Fd614611727cB831EF1a4Ac027` |
| HegicStrategy_STRIP_ETH_2 | `0xC01F11A80A79b6381c4AA3DD6E990f2ceb8decD6` | PriceCalculator_STRIP_ETH | `0x8CcB72CCF44343Fd614611727cB831EF1a4Ac027` |
| HegicStrategy_STRIP_ETH_3 | `0xe075abed5d13DbD331e0304A6d8caf1d92a2d3A6` | PriceCalculator_STRIP_ETH | `0x8CcB72CCF44343Fd614611727cB831EF1a4Ac027` |
| HegicStrategy_STRIP_ETH_4 | `0x13f47A8aCC11F27C7c8db89E45f07106F68ACb31` | PriceCalculator_STRIP_ETH | `0x8CcB72CCF44343Fd614611727cB831EF1a4Ac027` |

---

## 🔄 ETH INVERSE BEAR CALL SPREAD Strategies

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_INVERSE_BEAR_CALL_SPREAD_10_ETH | `0x43C38445233eBE18f4c7f80DB4a047e28fe8b6b2` | PriceCalculator_INVERSE_BEAR_CALL_SPREAD_10_ETH | `0x83F8F7BcCBDd0083eAC2b8BdD89f460794E51ae9` |
| HegicStrategy_INVERSE_BEAR_CALL_SPREAD_20_ETH | `0xD126ec906cEbCF9D8E60cbbE01428eFDDa04E637` | PriceCalculator_INVERSE_BEAR_CALL_SPREAD_20_ETH | `0xE984986327b0fBA63E0e65361E4937176014a970` |
| HegicStrategy_INVERSE_BEAR_CALL_SPREAD_30_ETH | `0x822bA6a1Aa169eAe19D925CC5427a49389639d31` | PriceCalculator_INVERSE_BEAR_CALL_SPREAD_30_ETH | `0xCE52F7DC25897F398eB5Bf65f5366E9ABc7C4784` |

---

## 🔄 ETH INVERSE BULL PUT SPREAD Strategies

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_INVERSE_BULL_PUT_SPREAD_10_ETH | `0x4837C736880D5f8C5B773495816f09407033Fb74` | PriceCalculator_INVERSE_BULL_PUT_SPREAD_10_ETH | `0xd0cf4Bfa6889BE64EbdFF9F5Dc5C20a4bf264a95` |
| HegicStrategy_INVERSE_BULL_PUT_SPREAD_20_ETH | `0x3C837a7Ec91C9Ebd16463D13a04060f2D6ED7B70` | PriceCalculator_INVERSE_BULL_PUT_SPREAD_20_ETH | `0x00985F243315D1CBB37aDD6Db044d4c002D99321` |
| HegicStrategy_INVERSE_BULL_PUT_SPREAD_30_ETH | `0x65903074e33c9D91d6dcdb04Db417093394589Bf` | PriceCalculator_INVERSE_BULL_PUT_SPREAD_30_ETH | `0xaEe44c4af01dbBd50b7bE594157Df0246B1b5E02` |

---

## 🔄 ETH INVERSE LONG BUTTERFLY Strategies

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_INVERSE_LONG_BUTTERFLY_10_ETH | `0x43F798Ea13b1C992c80965EF1e70f289E40F3Eff` | PriceCalculator_INVERSE_LONG_BUTTERFLY_10_ETH | `0x54c4043075E7B99Ea4688fF9715D7f7f170db915` |
| HegicStrategy_INVERSE_LONG_BUTTERFLY_20_ETH | `0xaaBfd6CAf65100600c90d02f66F22eE20A972215` | PriceCalculator_INVERSE_LONG_BUTTERFLY_20_ETH | `0x278c7Db349440ad3bE9D8847aeedCeaD982326fb` |
| HegicStrategy_INVERSE_LONG_BUTTERFLY_30_ETH | `0x23e039533Db1A9D68720C196c11d35C1edaA74F9` | PriceCalculator_INVERSE_LONG_BUTTERFLY_30_ETH | `0x6036F807f264471722c2F44b45Fd70Af32d7B027` |

---

## 🔄 ETH INVERSE LONG CONDOR Strategies

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_INVERSE_LONG_CONDOR_20_ETH | `0xDbFe2c1a9424287ED39Fa24E84cF5A24E222Ac93` | PriceCalculator_INVERSE_LONG_CONDOR_20_ETH | `0x9076Ab42f85b42a609183696f4a5E10f469f15b1` |
| HegicStrategy_INVERSE_LONG_CONDOR_30_ETH | `0xE2bfCdb466aa939c6B0D43ae928ee6E16509c045` | PriceCalculator_INVERSE_LONG_CONDOR_30_ETH | `0x66a693b704c52FaB6090Aa1d993B621acC789E6d` |

---

## 🔧 Price Calculator Contracts

| Price Calculator | Address | Used By |
|-----------------|---------|---------|
| **FlexiblePriceCalculator_CALL_100_ETH** | `0x62226cF9B0b6e8030FAe7e5C8d1371d103C0DDD9` | CALL 100% strategies |
| **FlexiblePriceCalculator_CALL_110_ETH** | `0xC5CaDAAF0434Dfb5b34E2bE7a19E17335c46bB20` | CALL 110% strategies |
| **FlexiblePriceCalculator_CALL_120_ETH** | `0xa454d66eEC60294cc1eb65D0F7c4cAAdF434FC02` | CALL 120% strategies |
| **FlexiblePriceCalculator_CALL_130_ETH** | `0xc4b95C7f85bfAF5F6956cB6c30Da775a3AEFb839` | CALL 130% strategies |
| **FlexiblePriceCalculator_PUT_100_ETH** | `0xF1f33827f06f81F4d1CF91FF097594108B5C7fb2` | PUT 100% strategies |
| **FlexiblePriceCalculator_PUT_90_ETH** | `0x1361eFa7A5Fdb9BAD4757fa3A29c5CBC7Fd0f400` | PUT 90% strategies |
| **FlexiblePriceCalculator_PUT_80_ETH** | `0x643a3fa00d519D9E3Ef5D96422889cE07d1b4528` | PUT 80% strategies |
| **FlexiblePriceCalculator_PUT_70_ETH** | `0x0447eb470d543a6b50Ab90B68b55A782Eea5B94e` | PUT 70% strategies |
| **PriceCalculator_SPREAD_CALL_10_ETH** | `0x0f93510B7221C2180F2E74298a17446ae9f1aE44` | SPREAD CALL 10% strategies |
| **PriceCalculator_SPREAD_CALL_20_ETH** | `0xf4509cC1c08f4Ec6F4509f0E5007db0c682D49B0` | SPREAD CALL 20% strategies |
| **PriceCalculator_SPREAD_CALL_30_ETH** | `0x10580f712fca2abCEABb8437032D08EB521a0474` | SPREAD CALL 30% strategies |
| **PriceCalculator_SPREAD_PUT_10_ETH** | `0x6D350e69DA0972371827f33a7DCD840f13360FfF` | SPREAD PUT 10% strategies |
| **PriceCalculator_SPREAD_PUT_20_ETH** | `0xD541A73572dD8bAD1E679b69d2DddEd08912Dd4f` | SPREAD PUT 20% strategies |
| **PriceCalculator_SPREAD_PUT_30_ETH** | `0x13b49eF04b13c24523CB39664EDf65e11aEd0908` | SPREAD PUT 30% strategies |
| **PriceCalculator_STRADDLE_ETH** | `0x95D56DD9C989152c39f0b2B423294a9511c99605` | STRADDLE strategies |
| **PriceCalculator_STRANGLE_10_ETH** | `0x6A89A5fBCAF77143f2930C34e0d2E6A17640D63C` | STRANGLE 10% strategies |
| **PriceCalculator_STRANGLE_20_ETH** | `0x199E71B4977731171D6411E5F8ab0BCd0fD51c8F` | STRANGLE 20% strategies |
| **PriceCalculator_STRANGLE_30_ETH** | `0x8aAb17D54570A804EAF8A6235359deEEb822F730` | STRANGLE 30% strategies |
| **PriceCalculator_STRAP_ETH** | `0x19AdFf4f004c118D96C983B848310C3dc27164B4` | STRAP strategies |
| **PriceCalculator_STRIP_ETH** | `0x8CcB72CCF44343Fd614611727cB831EF1a4Ac027` | STRIP strategies |
| **PriceCalculator_INVERSE_BEAR_CALL_SPREAD_10_ETH** | `0x83F8F7BcCBDd0083eAC2b8BdD89f460794E51ae9` | INVERSE BEAR CALL SPREAD 10% strategies |
| **PriceCalculator_INVERSE_BEAR_CALL_SPREAD_20_ETH** | `0xE984986327b0fBA63E0e65361E4937176014a970` | INVERSE BEAR CALL SPREAD 20% strategies |
| **PriceCalculator_INVERSE_BEAR_CALL_SPREAD_30_ETH** | `0xCE52F7DC25897F398eB5Bf65f5366E9ABc7C4784` | INVERSE BEAR CALL SPREAD 30% strategies |
| **PriceCalculator_INVERSE_BULL_PUT_SPREAD_10_ETH** | `0xd0cf4Bfa6889BE64EbdFF9F5Dc5C20a4bf264a95` | INVERSE BULL PUT SPREAD 10% strategies |
| **PriceCalculator_INVERSE_BULL_PUT_SPREAD_20_ETH** | `0x00985F243315D1CBB37aDD6Db044d4c002D99321` | INVERSE BULL PUT SPREAD 20% strategies |
| **PriceCalculator_INVERSE_BULL_PUT_SPREAD_30_ETH** | `0xaEe44c4af01dbBd50b7bE594157Df0246B1b5E02` | INVERSE BULL PUT SPREAD 30% strategies |
| **PriceCalculator_INVERSE_LONG_BUTTERFLY_10_ETH** | `0x54c4043075E7B99Ea4688fF9715D7f7f170db915` | INVERSE LONG BUTTERFLY 10% strategies |
| **PriceCalculator_INVERSE_LONG_BUTTERFLY_20_ETH** | `0x278c7Db349440ad3bE9D8847aeedCeaD982326fb` | INVERSE LONG BUTTERFLY 20% strategies |
| **PriceCalculator_INVERSE_LONG_BUTTERFLY_30_ETH** | `0x6036F807f264471722c2F44b45Fd70Af32d7B027` | INVERSE LONG BUTTERFLY 30% strategies |
| **PriceCalculator_INVERSE_LONG_CONDOR_20_ETH** | `0x9076Ab42f85b42a609183696f4a5E10f469f15b1` | INVERSE LONG CONDOR 20% strategies |
| **PriceCalculator_INVERSE_LONG_CONDOR_30_ETH** | `0x66a693b704c52FaB6090Aa1d993B621acC789E6d` | INVERSE LONG CONDOR 30% strategies |

---

## 📊 Strategy Configuration Summary

All ETH strategies are configured with:

- **Period Limits**: 1 hour (min) to 1 day (max)
- **Exercise Window**: 2 hours
- **Liquidity Limit**: 20,000 USDC per strategy
- **Price Scales**: 100% (ATM), 110% (10% OTM), 120% (20% OTM), 130% (30% OTM) for CALL
- **Price Scales**: 100% (ATM), 90% (10% OTM), 80% (20% OTM), 70% (30% OTM) for PUT

---
