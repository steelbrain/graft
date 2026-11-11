# examples

Two minimal kexts, one of each kind Graft serves. The guides walk through
them: [Write a bound consumer](../docs/guides/bound-consumer.md) and
[Write an owned client](../docs/guides/owned-client.md).
[docs/consumers.md](../docs/consumers.md) explains the two kinds.

| example | kind | what it shows |
|---|---|---|
| [hello-consumer](hello-consumer/README.md) | bound consumer | a class derived from a System-collection class, bound by Graft at boot from its manifest |
| [hello-client](hello-client/README.md) | owned client | a kext that calls Graft's C interface to look up a kernel symbol and publish its state |

Graft binds every placed kext that carries a manifest, so the consumer has a
bundle identifier of its own, `ai.aneesiqbal.graft.HelloConsumer`. Graft serves
calls only for the owned client `src/Policy.h` names, so the client passes
`ai.aneesiqbal.RgfxGate` in its calls. A client of your own needs that identity
too, or a Graft built with yours in `src/Policy.h`.

Each has its own Makefile and builds for x86-64 by default, or for arm64e with
`make ARCH='-arch arm64e'`. From the repository root, `make examples` builds
both for both architectures.
