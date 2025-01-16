### Registrar testnet

To install `pop-cli` for the testnet or use our deployed testnet, follow these steps:

#### 1. Clone and Run the Pop-CLI
```bash
git clone https://github.com/rotkonetworks/pop-cli
cd pop-cli
vim tests/networks/rococo+people.toml
```

With the following content
```
[relaychain]
chain = "rococo-local"

[[relaychain.nodes]]
name = "alice"
validator = true

[[relaychain.nodes]]
name = "bob"
validator = true

[[parachains]]
id = 1004
chain = "people-rococo-local"

[[parachains.collators]]
name = "people-01"
args = [
    "--pruning=archive"
]
```

Then continue building the local testnet
```
cargo run up parachain --file tests/networks/rococo+people.toml --verbose
```
#### 2. Set WebSocket Endpoint
Use either the provided endpoint or your local testnet for `people-rococo`:
Use either the provided endpoint/portal or your local testnet for `people-rococo`:
```
wss://dev.rotko.net/people-rococo
```

#### 3. Generate Call Data
In the Polkadot UI, navigate to **Extrinsics** and create a transaction to add a registrar. Copy the **calldata** from the generated transaction.
![image](https://hackmd.io/_uploads/SJbMbCfk1x.png)

Example transaction for call data extraction:
[Extrinsics decode tool](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fdev.rotko.net%2Fpeople-rococo#/extrinsics/decode/0x3200001cbd2d43530a44705ad088af313e18f80b53ef16b36177cd4b77b846f2a5f07c)

#### 4. Relaychain Sudo Rights Requirement
Executing the above call from a local parachain account will fail due to lack of rights. You need sudo access at the **relaychain** level.

#### 5. Create a Sudo Call on the Relaychain
Go to the relaychain’s [Sudo page](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fdev.rotko.net%2Frococo#/sudo) and submit a sudo call with the following XCM transaction:

```rust
xcmPallet::send(
    dest: XcmVersionedLocation::V4(StagingXcmV4Location {
        parents: 0,
        interior: StagingXcmV4Junctions::X1([Lookup71::Parachain(Compact(1004))])
    }),
    message: XcmVersionedXcm::V4(StagingXcmV4Xcm {
        0: StagingXcmV4Instruction::UnpaidExecution {
            weightLimit: XcmV3WeightLimit::Unlimited,
            checkOrigin: None
        },
        1: StagingXcmV4Instruction::Transact {
            originKind: XcmV3OriginKind::Superuser,
            requireWeightAtMost: SpWeightsWeightV2Weight {
                refTime: Compact(5000000000),
                proofSize: Compact(50000)
            },
            call: XcmDoubleEncoded::new(Bytes::from_hex("0x3200001cbd2d43530a44705ad088af313e18f80b53ef16b36177cd4b77b846f2a5f07c"))
        }
    })
);
```

Submit this sudo call as **Alice** (the first validator in the network):
![image](https://hackmd.io/_uploads/H1MAQAf1Jg.png)

#### 6. Verify Registrar Creation
Watch the [Explorer](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fpaseo-people.dotters.network%2F#/explorer) for events confirming the registrar was created on the parachain (people-rococo).
