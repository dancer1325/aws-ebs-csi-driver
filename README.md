# Amazon Elastic Block Store (EBS) CSI driver
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/kubernetes-sigs/aws-ebs-csi-driver)](https://github.com/kubernetes-sigs/aws-ebs-csi-driver/releases)
[![Go Report Card](https://goreportcard.com/badge/github.com/kubernetes-sigs/aws-ebs-csi-driver)](https://goreportcard.com/report/github.com/kubernetes-sigs/aws-ebs-csi-driver)

* ⚠️EBS CSI Driver support | [AWS Snow Family devices](https://aws.amazon.com/snowball/) is deprecated ⚠️
  * NO further Snow-specific bugfixes OR feature requests
  * | v1.44, EXISTING functionality / Snow devices -- will be -- removed 
  * NOT affect the support | OTHER platforms
    * _Example:_ [Amazon EC2](https://aws.amazon.com/ec2/) OR [AWS Outposts](https://aws.amazon.com/outposts/)
  * see [#2365](https://github.com/kubernetes-sigs/aws-ebs-csi-driver/issues/2365)

## Overview

* provides a [CSI](https://github.com/container-storage-interface/spec/blob/master/spec.md) 
  * used by Container Orchestrators -- to -- manage the lifecycle of Amazon EBS volumes

## Features
* **Static Provisioning**
  * EXTERNALLY-created EBS volume -- is associated with a -- [PersistentVolume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) (PV) / 
    * used | Kubernetes
* **Dynamic Provisioning**
  * AUTOMATICALLY
    * create EBS volumes
      * if you want fine-grained control -> pass -- , via [StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/#the-storageclass-resource), -- parameters 
    * EBS volumes, from [PersistentVolumeClaims](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#dynamic)) (PVC) -- are associated to -- [PersistentVolumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) (PV)
* **Mount Options**
  * specified | [PersistentVolume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) (PV)
* **Block Volumes** 
  * == EBS volume -- are consumed as a -- [raw block device](https://kubernetes-csi.github.io/docs/raw-block.html)
* **Volume Snapshots** 
  * == [Kubernetes volume snapshots](https://kubernetes.io/docs/concepts/storage/volume-snapshots/)
  * are
    * created
    * restored 
* **Volume Resizing**
  * -- by -- specifying a NEW size | [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#expanding-persistent-volumes-claims) (PVC)
* **Volume Modification**
  * == change properties (type, iops, or throughput) 
  * -- via -- [`VolumeAttributesClass`](examples/kubernetes/modify-volume)

## Container Images

| Driver Version | [registry.k8s.io](https://kubernetes.io/blog/2022/11/28/registry-k8s-io-faster-cheaper-ga/) Image | [ECR Public](https://gallery.ecr.aws/ebs-csi-driver/aws-ebs-csi-driver) Image |
|----------------|---------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| v1.43.0        | registry.k8s.io/provider-aws/aws-ebs-csi-driver:v1.43.0                                           | public.ecr.aws/ebs-csi-driver/aws-ebs-csi-driver:v1.43.0                      |
| v1.42.0        | registry.k8s.io/provider-aws/aws-ebs-csi-driver:v1.42.0                                           | public.ecr.aws/ebs-csi-driver/aws-ebs-csi-driver:v1.42.0                      |

## Releases

* monthly releases
  * MINIMUM, a `MINOR` version bump
* unscheduled releases
  * use cases
    * patches to security vulnerabilities

* follows [semantic versioning](https://semver.org/)
  * SIGNIFICANT breaking changes -> `MAJOR` update
  * NEW features -> `MINOR` update
  * Bug or vulnerability fixes -> `PATCH` update

## Support

* | 
  * latest version
  * latest -1 version 
* bugs or vulnerabilities | latest version,
  * | latest -1, backported -- via -- NEW minor version

* this support policy can change

## Compatibility

* compatible with ALL Kubernetes versions -- supported by --
  * [Kubernetes project](https://kubernetes.io/releases/) & / OR
  * [Amazon EKS (including extended support versions)](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html)

* EBS CSI Driver implements the [Container Storage Interface specification](https://github.com/container-storage-interface/spec/blob/master/spec.md) `v1.9.0`

## Documentation

* [Driver Installation](docs/install.md)
* [Driver Launch Options](docs/options.md)
* [StorageClass Parameters](docs/parameters.md)
* [Frequently Asked Questions](docs/faq.md)
* [Volume Tagging](docs/tagging.md)
* [Volume Modification](docs/modify-volume.md)
* [Kubernetes Examples](/examples/kubernetes)
* [Driver Uninstallation](docs/install.md#uninstalling-the-ebs-csi-driver)
* [Development and Contributing](CONTRIBUTING.md)
