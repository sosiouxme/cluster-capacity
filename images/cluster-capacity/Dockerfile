FROM registry.svc.ci.openshift.org/openshift/release:golang-1.10 AS builder
WORKDIR /go/src/github.com/kubernetes-incubator/cluster-capacity
COPY . .
RUN make build

FROM registry.svc.ci.openshift.org/openshift/origin-v4.0:base
COPY --from=builder /go/src/github.com/kubernetes-incubator/cluster-capacity/_output/local/bin/linux/amd64/hypercc /usr/bin/
RUN ln -sf /usr/bin/hypercc /usr/bin/cluster-capacity
RUN ln -sf /usr/bin/hypercc /usr/bin/genpod
CMD ["/usr/bin/cluster-capacity", "--help"]
