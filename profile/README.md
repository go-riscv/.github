<p align="center">
<a href="https://go-faster.org"><img src="logo_borderless.svg" width="256" height="105" alt="go faster logo"></a>
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
Starting from go1.21.0, official port is provided. Use [go.dev/dl](https://go.dev/dl/) under "Other Ports".

### Distroless

See [packages][distroless-packages] from [go-rsicv/distroless][distroless-repo] repository:

```dockerfile
FROM ghcr.io/go-riscv/distroless/static-unstable:nonroot
```

```dockerfile
FROM ghcr.io/go-riscv/distroless/static-unstable:latest
```

### Go image
See [go-riscv/docker-library-go][docker-package]. Based on `riscv64/buildpack-deps:sid-scm` image.

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

### etcd

See [packages][etcd-packages] from [go-riscv/etcd][etcd-repo] repository:

```dockerfile
FROM ghcr.io/go-riscv/etcd:v3.6.0-riscv64.0-riscv64
```

[etcd-repo]: https://github.com/go-riscv/etcd
[etcd-packages]: https://github.com/go-riscv/etcd/pkgs/container/etcd

## Roadmap
###  Long-term

Complete support for `riscv64`, ETA late 2025.

- [x] `riscv64` downloads  are available on [golang.org](https://golang.org/dl/) ([golang/go#53862][go-issue])
- [x] [riscv64 port](https://wiki.debian.org/Ports/riscv64) becomes official
- [ ] [protobuf][protobuf] adds support for `riscv64` ([issue][protobuf-issue], [PR][protobuf-pr])
- [x] debian 13 (trixie) is [released](https://en.wikipedia.org/wiki/Debian_version_history) in ~2025
- [ ] [distroless](https://github.com/GoogleContainerTools/distroless/) adds support for  debian13 and `riscv64`
- [ ] [docker "Official Image" for Go](https://github.com/docker-library/golang) is available for `riscv64`
- [ ] [etcd][etcd] project adds support for `riscv64` ([PR][etcd-pr])
- [ ] [kubernetes/release][k8s-release] adds support for `riscv64` ([PR][k8s-release-pr])
- [ ] [kubernetes][k8s] project adds support for `riscv64` ([PR][k8s-pr])
- [ ] [cilium][cilium] project adds support for `riscv64` ([issue][cilium-issue], [PR][cilium-pr])

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


#### Issues and PRs

Links:

- https://github.com/carlosedp/riscv-bringup/
- https://lists.debian.org/debian-riscv/2023/03/msg00001.html

Issues and PR's:

- https://github.com/golang/go/issues/59113
- https://github.com/golang/go/issues/53862
- https://github.com/golang/go/issues/59317
- https://github.com/kubernetes-sigs/cri-tools/pull/1116
- https://github.com/etcd-io/etcd/pull/15490
- https://github.com/protocolbuffers/protobuf/pull/12244
- https://github.com/protocolbuffers/protobuf/issues/12266
- https://github.com/GoogleContainerTools/distroless/pull/1268
- https://github.com/GoogleContainerTools/distroless/issues/1269
- https://github.com/kubernetes/release/pull/2968
- https://github.com/cilium/cilium/issues/24434
- https://github.com/cilium/cilium/pull/24436
- https://github.com/golang/go/issues/59113
- https://github.com/docker-library/golang/issues/455
- https://github.com/docker-library/golang/issues/435
- https://github.com/docker-library/official-images/pull/10502
- https://github.com/prometheus/node_exporter/issues/2645
