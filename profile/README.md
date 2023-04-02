<p align="center">
<a href="https://go-faster.org"><img src="./profile/logo_borderless.svg" width="256" height="105" alt="go faster logo"></a>
</p>

The [Go Faster](https://github.com/go-faster/) initiative to bring RISC-V (`riscv64`) to Go and Kubernetes ecosystem.

Kudos to [carlosedp](https://github.com/carlosedp) for his great [riscv-bringup](https://github.com/carlosedp/riscv-bringup/)!

*NB: This organization is not officially affiliated with [RISC-V](https://riscv.org/) project.*

## Signing keys

See [943040B9817AC4C7][keyserver] on keyserver.ubuntu.com:

[keyserver]: https://keyserver.ubuntu.com/pks/lookup?search=943040B9817AC4C7&fingerprint=on&op=index

```
gpg --batch --keyserver keyserver.ubuntu.com --recv-keys '943040B9817AC4C7'
```

```
pub   dsa2048 2023-03-20 [SC] [expires: 2028-03-18]
      7B7C86E59840A829F7657100943040B9817AC4C7
uid           [ unknown] go-riscv (Key for https://github.com/go-riscv) <riscv@go-faster.org>
sub   rsa4096 2023-04-02 [E] [expires: 2028-03-31]
sub   rsa4096 2023-04-02 [S] [expires: 2028-03-31]
sub   elg2048 2023-03-20 [E] [expires: 2028-03-18]
```

Cosign public key:

```
wget https://github.com/go-riscv/.github/raw/main/cosign.pub
```
```
-----BEGIN PUBLIC KEY-----
MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEoToNKAqA+QN2yTBN1HKBLTEd1aDJ
32hM/MJHmNf4Y/8R5ZpOM+Lo+OGykd/4ZsJU5T+Kp441UKN0fKZFTi9aZA==
-----END PUBLIC KEY-----
```

## Releases

### Go
Grab [latest release][go-latest] from [go-riscv/go][go-repo] repository:

| File name                                                                                                                        | Kind        | Size      | SHA256                                                               |
|----------------------------------------------------------------------------------------------------------------------------------|-------------|-----------|----------------------------------------------------------------------|
| [**go1.20.2.linux-riscv64.tar.gz**](https://github.com/go-riscv/go/releases/download/build-230402/go1.20.2.linux-riscv64.tar.gz) | **Archive** | **154MB** | **024b9a98d7e2facc553bd9b00cd8ccbc22c82248c4d85f0b6a89b5eafc5715d2** |
| [go-linux-riscv64-bootstrap.tbz](https://github.com/go-riscv/go/releases/download/build-230402/go-linux-riscv64-bootstrap.tbz)   | Bootstrap   | 88MB      | d06f0c6e6d9a141271f41d61a8d0e813cc8f162e9a2d7bf119c40ee3e7a5c2b8     |
| [go1.20.2.src.tar.gz](https://github.com/go-riscv/go/releases/download/build-230402/go1.20.2.src.tar.gz)                         | Source      | 24MB      | 4d0e2850d197b4ddad3bdb0196300179d095bb3aefd4dfbc3b36702c3728f8ab     |

[go-repo]: https://github.com/go-riscv/go
[go-latest]: https://github.com/go-riscv/go/releases/latest

### Distroless

See [packages][distroless-packages] from [go-rsicv/distroless][distroless-repo] repository:

```dockerfile
FROM ghcr.io/go-riscv/distroless/static-unstable:nonroot
```

```dockerfile
FROM ghcr.io/go-riscv/distroless/static-unstable:latest
```

### Go image
See [go-riscv/go][docker-package]. Based on `riscv64/buildpack-deps:sid-scm` image.

Tags: `1.20.2`, `1.20`, `latest`

[docker-package]: https://github.com/go-riscv/docker-library-go/pkgs/container/go

```dockerfile
FROM ghcr.io/go-riscv/go:1.20
```

[distroless-packages]: https://github.com/orgs/go-riscv/packages?repo_name=distroless
[distroless-repo]: https://github.com/go-riscv/distroless

### Busybox

Grab [latest release][busybox-latest] from [go-riscv/busybox][busybox-repo] repository.

[busybox-repo]: https://github.com/go-riscv/busybox
[busybox-latest]: https://github.com/go-riscv/busybox/releases/latest

## Roadmap
###  Long-term

Complete support for `riscv64`, ETA late 2025.

1. [protobuf][protobuf] adds support for `riscv64` ([issue][protobuf-issue], [PR][protobuf-pr])
2. `riscv64` downloads  are available on [golang.org](https://golang.org/dl/) ([golang/go#53862][go-issue])
3. [riscv64 port](https://wiki.debian.org/Ports/riscv64) becomes stable
4. debian 13 (trixie) is [released](https://en.wikipedia.org/wiki/Debian_version_history) in ~2025
5. [distroless](https://github.com/GoogleContainerTools/distroless/) adds support for  debian13 and `riscv64`
6. [docker "Official Image" for Go](https://github.com/docker-library/golang) is available for `riscv64`
7. [etcd][etcd] project adds support for `riscv64` ([PR][etcd-pr])
8. [kubernetes/release][k8s-release] adds support for `riscv64` ([PR][k8s-release-pr])
9. [kubernetes][k8s] project adds support for `riscv64` ([PR][k8s-pr])
10. [cilium][cilium] project adds support for `riscv64` ([issue][cilium-issue], [PR][cilium-pr])

[go-issue]: https://github.com/golang/go/issues/53862
[protobuf]: https://github.com/protocolbuffers/protobuf
[protobuf-issue]: https://github.com/protocolbuffers/protobuf/issues/12266
[protobuf-pr]: https://github.com/protocolbuffers/protobuf/pull/12244
[etcd]: https://github.com/etcd-io/etcd
[etcd-pr]: https://github.com/etcd-io/etcd/pull/15490
[k8s-release]: https://github.com/kubernetes/release
[k8s-release-pr]: https://github.com/kubernetes/release/pull/2968
[k8s]: https://github.com/kubernetes/kubernetes
[k8s-pr]: https://github.com/kubernetes/kubernetes/pull/116686
[cilium]: https://github.com/cilium/cilium
[cilium-issue]: https://github.com/cilium/cilium/issues/24434
[cilium-pr]: https://github.com/cilium/cilium/pull/24436

### Short-term

Setup CI/CD pipeline for `riscv64` artifacts and host them here until they are upstreamed.

- [x] Distroless images
- [x] Busybox
- [x] Docker "Official Image" for Go
- [ ] Image: etcd
- [ ] Kubernetes base images
- [ ] Kubernetes release artifacts (kubelet, kubeadm, kubectl, ...)
- [ ] Cilium binaries
- [ ] Cilium images