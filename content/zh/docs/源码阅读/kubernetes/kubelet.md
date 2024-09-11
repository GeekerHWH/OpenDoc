---
title: Kubelet
date: 2017-01-05
description: >
  Kubernetes体系中最重要的角色，下与CRI/CNI/CSI打交道，上与api-server通讯，真正掌管Pod死活
  的组件！
categories: [Cloud Native]
tags: [Kubernetes]
weight: 2
---

### Kubelet启动过程
主启动函数 [NewMainKubelet](https://github.com/kubernetes/kubernetes/blob/master/pkg/kubelet/kubelet.go)

```go
func NewMainKubelet(kubeCfg *kubeletconfiginternal.KubeletConfiguration,
	kubeDeps                                           *Dependencies,
	crOptions                                          *config.ContainerRuntimeOptions,
	hostname                                           string,
	hostnameOverridden                                 bool,
	nodeName                                           types.NodeName,
	nodeIPs                                            []net.IP,
	providerID                                         string,
	cloudProvider                                      string,
	certDirectory                                      string,
	rootDirectory                                      string,
	podLogsDirectory                                   string,
	imageCredentialProviderConfigFile                  string,
	imageCredentialProviderBinDir                      string,
	registerNode                                       bool,
	registerWithTaints                                 []v1.Taint,
	allowedUnsafeSysctls                               []string,
	experimentalMounterPath                            string,
	kernelMemcgNotification                            bool,
	experimentalNodeAllocatableIgnoreEvictionThreshold bool,
	minimumGCAge                                       metav1.Duration,
	maxPerPodContainerCount                            int32,
	maxContainerCount                                  int32,
	registerSchedulable                                bool,
	nodeLabels                                         map[string]string,
	nodeStatusMaxImages                                int32,
	seccompDefault                                     bool,
) (*Kubelet, error)
```
启动过程示意图
![启动过程](/images/kubelet/kubelet.png)