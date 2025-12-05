## �� Core Contracts

| # | Contract Name | Address | Purpose |
|---|---------------|---------|---------|
| 1 | **CoverPool** | `0x1C786D28341340e6A9b47ddB8c3e20E719562BB5` | USDC liquidity pool for backstop coverage |
| 2 | **ProfitDistributor** | `0xFF9031382D9cdd44A95FC6e5EbE74BF2C3591069` | Distributes profits to LPs |
| 3 | **PositionsManager** | `0x82e01f039Caa5e423810B48B2b0fCA98Bb5e230e` | ERC721 NFT manager for options |
| 4 | **ProfitCalculator** | `0xDb7D577F1345AD74B125501F4B68240F44ed7e60` | Calculates option payoffs |
| 5 | **LimitController** | `0x06d275553219068F4186a71B92200FeA2Ec17Ed5` | Controls strategy limits |
| 6 | **OperationalTreasury** | `0xdE19737db2325DD2aA072713aEaa7db4F4b23009` | ⭐ **Main contract** - Creates and settles options |

---

## �� Token & Oracle Contracts

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

## �� ETH CALL Strategies

### CALL 100% (ATM - At The Money)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_CALL_100_ETH_1 | `0x4aA2dB24AdC9c2ad0d5C10A96121093Dee810Ea5` | PriceCalculator_CALL_100_ETH | `0xA59180C506A9C89DB47E49A332d2363F8288c1Af` |
| HegicStrategy_CALL_100_ETH_2 | `0x79d07802E6C2f7AC48153248547829c71Ac43550` | PriceCalculator_CALL_100_ETH | `0xA59180C506A9C89DB47E49A332d2363F8288c1Af` |
| HegicStrategy_CALL_100_ETH_3 | `0x8e7CBEdeFa8Af10f223Cc3e7F962C6Dad807373B` | PriceCalculator_CALL_100_ETH | `0xA59180C506A9C89DB47E49A332d2363F8288c1Af` |
| HegicStrategy_CALL_100_ETH_4 | `0xF3385D57fA2558964c7c279C91eA6FeF9730dcD9` | PriceCalculator_CALL_100_ETH | `0xA59180C506A9C89DB47E49A332d2363F8288c1Af` |

### CALL 110% (10% OTM - Out of The Money)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_CALL_110_ETH_1 | `0x8D8421b549FC8bf29c257A192e072Db8881a181D` | PriceCalculator_CALL_110_ETH | `0x903E122119F53F87c8017B23EEC2C3496A9F05c6` |
| HegicStrategy_CALL_110_ETH_2 | `0x464833AcfE300A3F48aE2c8c9072b033e11257d6` | PriceCalculator_CALL_110_ETH | `0x903E122119F53F87c8017B23EEC2C3496A9F05c6` |
| HegicStrategy_CALL_110_ETH_3 | `0x8CE876f237c63726125E959580c5b5BDe748d72a` | PriceCalculator_CALL_110_ETH | `0x903E122119F53F87c8017B23EEC2C3496A9F05c6` |
| HegicStrategy_CALL_110_ETH_4 | `0x277877cDba755EFCEfFC2a47A9A4a5294331BF58` | PriceCalculator_CALL_110_ETH | `0x903E122119F53F87c8017B23EEC2C3496A9F05c6` |

### CALL 120% (20% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_CALL_120_ETH_1 | `0x3c8a1C67d81385A4c66966900b9a8f47Ed5ed29B` | PriceCalculator_CALL_120_ETH | `0xb59476b53351Cd1b26ead70835E5ED7B8929b409` |
| HegicStrategy_CALL_120_ETH_2 | `0x58eB94dA4e631d9Ad18a8cD446894D8Ec0dd4bbb` | PriceCalculator_CALL_120_ETH | `0xb59476b53351Cd1b26ead70835E5ED7B8929b409` |
| HegicStrategy_CALL_120_ETH_3 | `0x1b9493A0a6cfb80D6b7Fb958A695198399620Eb9` | PriceCalculator_CALL_120_ETH | `0xb59476b53351Cd1b26ead70835E5ED7B8929b409` |
| HegicStrategy_CALL_120_ETH_4 | `0x7925804d0bE796d7a10627527Fd4D04ebbe2ED4E` | PriceCalculator_CALL_120_ETH | `0xb59476b53351Cd1b26ead70835E5ED7B8929b409` |

### CALL 130% (30% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_CALL_130_ETH_1 | `0x22ea8743fC5fA78Fc95cb0F9aF53B72195220d11` | PriceCalculator_CALL_130_ETH | `0xFfBae80a2D49BeF876509fad228cC6DAC582934E` |
| HegicStrategy_CALL_130_ETH_2 | `0x3D48c7f0F7b781ef5633945c6Dc93FB7F24C7d6B` | PriceCalculator_CALL_130_ETH | `0xFfBae80a2D49BeF876509fad228cC6DAC582934E` |
| HegicStrategy_CALL_130_ETH_3 | `0xe59eFe044c48a56D00f12BA449aBf0C1cB394946` | PriceCalculator_CALL_130_ETH | `0xFfBae80a2D49BeF876509fad228cC6DAC582934E` |
| HegicStrategy_CALL_130_ETH_4 | `0x0281396746A4375Eb547C63210985Cdf58df8175` | PriceCalculator_CALL_130_ETH | `0xFfBae80a2D49BeF876509fad228cC6DAC582934E` |

---

## �� ETH PUT Strategies

### PUT 100% (ATM - At The Money)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_PUT_100_ETH_1 | `0x71737F6bE4095bB11e17EA30D90952150d48CEf2` | PriceCalculator_PUT_100_ETH | `0xDCCd37e49123071fcb0396299Bbe8544d0FB7b43` |
| HegicStrategy_PUT_100_ETH_2 | `0x0dc0271b96588AEB478FE16Ae0df0F91944F7041` | PriceCalculator_PUT_100_ETH | `0xDCCd37e49123071fcb0396299Bbe8544d0FB7b43` |
| HegicStrategy_PUT_100_ETH_3 | `0xC88426abC1a8962d4d33FBEc8D4b593af3d11cC3` | PriceCalculator_PUT_100_ETH | `0xDCCd37e49123071fcb0396299Bbe8544d0FB7b43` |
| HegicStrategy_PUT_100_ETH_4 | `0x59D2Eed270742b48971DF08d65aec9327c41a20B` | PriceCalculator_PUT_100_ETH | `0xDCCd37e49123071fcb0396299Bbe8544d0FB7b43` |

### PUT 90% (10% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_PUT_90_ETH_1 | `0x506d76E67Cc29519917F741c5709DA184E0E3d20` | PriceCalculator_PUT_90_ETH | `0x7aA123BE6d53d8A7431a45AFfEB29C50896847d8` |
| HegicStrategy_PUT_90_ETH_2 | `0x1304E97Ab92d83F256e3623aC4E27aeB364bC44A` | PriceCalculator_PUT_90_ETH | `0x7aA123BE6d53d8A7431a45AFfEB29C50896847d8` |
| HegicStrategy_PUT_90_ETH_3 | `0x90cA27468527C5044f4d05DB051206793AeDcdeb` | PriceCalculator_PUT_90_ETH | `0x7aA123BE6d53d8A7431a45AFfEB29C50896847d8` |
| HegicStrategy_PUT_90_ETH_4 | `0x0456530b44a80DC88D5410A1B627F8FA4B8530Ac` | PriceCalculator_PUT_90_ETH | `0x7aA123BE6d53d8A7431a45AFfEB29C50896847d8` |

### PUT 80% (20% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_PUT_80_ETH_1 | `0x4bF787797843796a988BDd857Ed20769841f4D96` | PriceCalculator_PUT_80_ETH | `0x34434b4d4e2b69241562e1fd16968acA05e921c0` |
| HegicStrategy_PUT_80_ETH_2 | `0x7b396964cc333CC0EBC37Ff271070C93E421e08D` | PriceCalculator_PUT_80_ETH | `0x34434b4d4e2b69241562e1fd16968acA05e921c0` |
| HegicStrategy_PUT_80_ETH_3 | `0x169c84f4Fcfd61894B1E9ccAe1a4F668cB911914` | PriceCalculator_PUT_80_ETH | `0x34434b4d4e2b69241562e1fd16968acA05e921c0` |
| HegicStrategy_PUT_80_ETH_4 | `0xedd861Ee1aC915bD89286EF1cfcE9DFeCF1E8499` | PriceCalculator_PUT_80_ETH | `0x34434b4d4e2b69241562e1fd16968acA05e921c0` |

### PUT 70% (30% OTM)

| Strategy | Address | Price Calculator | Calculator Address |
|----------|---------|------------------|-------------------|
| HegicStrategy_PUT_70_ETH_1 | `0xA35047FE5178c6D2d4B6465937d02DF46151621C` | PriceCalculator_PUT_70_ETH | `0x626fBdc6E45414b7Ca0f2013b705f0e25040a14D` |
| HegicStrategy_PUT_70_ETH_2 | `0xCE4A8FC81bd300BD0719EACBBE946962fD79FDF3` | PriceCalculator_PUT_70_ETH | `0x626fBdc6E45414b7Ca0f2013b705f0e25040a14D` |
| HegicStrategy_PUT_70_ETH_3 | `0x16b7211E02D094C214414E5227655DA873443670` | PriceCalculator_PUT_70_ETH | `0x626fBdc6E45414b7Ca0f2013b705f0e25040a14D` |
| HegicStrategy_PUT_70_ETH_4 | `0x2A1A1fBDc95678E0fC2e174D915f18284A757F77` | PriceCalculator_PUT_70_ETH | `0x626fBdc6E45414b7Ca0f2013b705f0e25040a14D` |

---

## �� Price Calculator Contracts

| Price Calculator | Address | Used By |
|-----------------|---------|---------|
| PriceCalculator_CALL_100_ETH | `0xA59180C506A9C89DB47E49A332d2363F8288c1Af` | CALL 100% strategies |
| PriceCalculator_CALL_110_ETH | `0x903E122119F53F87c8017B23EEC2C3496A9F05c6` | CALL 110% strategies |
| PriceCalculator_CALL_120_ETH | `0xb59476b53351Cd1b26ead70835E5ED7B8929b409` | CALL 120% strategies |
| PriceCalculator_CALL_130_ETH | `0xFfBae80a2D49BeF876509fad228cC6DAC582934E` | CALL 130% strategies |
| PriceCalculator_PUT_100_ETH | `0xDCCd37e49123071fcb0396299Bbe8544d0FB7b43` | PUT 100% strategies |
| PriceCalculator_PUT_90_ETH | `0x7aA123BE6d53d8A7431a45AFfEB29C50896847d8` | PUT 90% strategies |
| PriceCalculator_PUT_80_ETH | `0x34434b4d4e2b69241562e1fd16968acA05e921c0` | PUT 80% strategies |
| PriceCalculator_PUT_70_ETH | `0x626fBdc6E45414b7Ca0f2013b705f0e25040a14D` | PUT 70% strategies |
