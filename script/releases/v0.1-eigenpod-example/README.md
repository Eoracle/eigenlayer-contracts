# v0.1-eigenpod-example

This is an example of how to write a deploy-queue-upgrade series of scripts using [Zeus](https://github.com/Layr-Labs/zeus). **THIS IS PURELY DEMONSTRATIVE. DO NOT USE THIS FOR PRODUCTION PURPOSES.**

## How to Run

To begin, run the following command from this directory:

```sh
export $(cat .env.example | xargs)
```

This will populate your environment with example environment variables.

If running with Zeus, then Zeus should auto-populate your environment for you, and this step is not necessary.

### Commands

For the deploy script (the first script), run:

```sh
forge script 1-eoa.s.sol -s "deploy()"
```

You can expect an output similar to:

```txt
Script ran successfully.
Gas used: 6407912

== Return ==
0: struct EOADeployer.Deployment[] [Deployment({ deployedTo: 0x90193C961A926261B756D1E5bb255e67ff9498A1, overrideName: "", singleton: true }), Deployment({ deployedTo: 0xA8452Ec99ce0C64f20701dB7dD3abDb607c00496, overrideName: "", singleton: true })]
```

To run the queue script (the second script), run:

```sh
forge script script/releases/v0.1-eigenpod-example/2-multisig.s.sol -s "execute()"
```

Example output:

```txt
Script ran successfully.
Gas used: 1005076

== Return ==
0: struct SafeTx SafeTx({ to: 0x40A2aCCbd92BCA938b02010E17A5b8929b49130D, value: 0, data: 0x8d80ff0a00000000000000000000000000000000000000000000000000000000000000200000000000000000000000000000000000000000000000000000000000000419000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000003c43a66f901000000000000000000000000da29bb71669f46f2a779b4b62f03644a84ee3479000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000a000000000000000000000000000000000000000000000000000000000000000c0ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002c48d80ff0a000000000000000000000000000000000000000000000000000000000000006000000000000000000000000040a2accbd92bca938b02010e17a5b8929b49130d000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002248d80ff0a000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000001d2001bef05c7303d44e0e2fcd2a19d993eded4c51b5b000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001049623609d000000000000000000000000b8d8952f572e67b11e43bc21250967772fa883ff00000000000000000000000010eba780ccd9e5e9ffbe529c25046c076be91048000000000000000000000000000000000000000000000000000000000000006000000000000000000000000000000000000000000000000000000000000000641794bb3c000000000000000000000000da29bb71669f46f2a779b4b62f03644a84ee34790000000000000000000000009ab2feaf0465f0ed51fc2b663ef228b418c9dad10000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000092cc4a800a1513e85c481dddf3a06c6921211eac000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000243659cfe60000000000000000000000008da4b953cbfb715624d98c0d2b4a7978462efd380000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000, op: 1 })
```

For the execute step (the third step), run:

```sh
forge script script/releases/v0.1-eigenpod-example/3-multisig.s.sol -s "execute()"
```

Example output:

```txt
Script ran successfully.
Gas used: 984745

== Return ==
0: struct SafeTx SafeTx({ to: 0x40A2aCCbd92BCA938b02010E17A5b8929b49130D, value: 0, data: 0x8d80ff0a000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000003d2000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000003240825f38f000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000002c48d80ff0a000000000000000000000000000000000000000000000000000000000000006000000000000000000000000040a2accbd92bca938b02010e17a5b8929b49130d000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002248d80ff0a000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000001d2001bef05c7303d44e0e2fcd2a19d993eded4c51b5b000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001049623609d000000000000000000000000b8d8952f572e67b11e43bc21250967772fa883ff00000000000000000000000010eba780ccd9e5e9ffbe529c25046c076be91048000000000000000000000000000000000000000000000000000000000000006000000000000000000000000000000000000000000000000000000000000000641794bb3c000000000000000000000000da29bb71669f46f2a779b4b62f03644a84ee34790000000000000000000000009ab2feaf0465f0ed51fc2b663ef228b418c9dad10000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000092cc4a800a1513e85c481dddf3a06c6921211eac000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000243659cfe60000000000000000000000008da4b953cbfb715624d98c0d2b4a7978462efd380000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000b8d8952f572e67b11e43bc21250967772fa883ff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000004715018a60000000000000000000000000000, op: 1 })
```