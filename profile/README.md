<p align="center">
<a href="https://go-faster.org"><img src="./profile/logo_borderless.svg" width="256" height="105" alt="go faster logo"></a>
</p>

The [Go Faster](https://github.com/go-faster/) initiative to bring RISC-V (`riscv64`) to Go and Kubernetes ecosystem.

Kudos to [carlosedp](https://github.com/carlosedp) for his great [riscv-bringup](https://github.com/carlosedp/riscv-bringup/)!

*NB: This organization is not officially affiliated with [RISC-V](https://riscv.org/) project.*

## Roadmap
###  Long-term

Complete support for `riscv64`.

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
- [ ] Docker "Official Image" for Go
- [ ] Image: etcd
- [ ] Kubernetes base images
- [ ] Kubernetes release artifacts (kubelet, kubeadm, kubectl, ...)
- [ ] Cilium binaries
- [ ] Cilium images