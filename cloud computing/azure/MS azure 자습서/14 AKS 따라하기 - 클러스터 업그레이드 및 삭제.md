# 14. AKS 따라하기 - 클러스터 업그레이드 및 삭제

### 현재 버전과 사용가능한 클러스터 버전 가져오기

```java
az aks get-upgrades --resource-group myResourceGroup --name myAKSCluster
```

- 해당 명령어 실행시 현재 이용가능한 추후 버전을 보여준다.
- 이걸 토대로 수동 업그레이드 명령어를 실행

```java
az aks upgrade --resource-group myResourceGroup --name myAKSCluster --kubernetes-version KUBERNETES_VERSION
```

### 자동 업테이트 설정하기

```java
az aks update --resource-group myResourceGroup --name myAKSCluster --auto-upgrade-channel patch
```

### 업그레이드 이벤트 보기 및 업그레이드 여부 파악 하기

- 기본 네임스페이스에서 업그레이드 이벤트를 확인하기

```java
kubectl get events --field-selector source=upgrader
```

- 현재 버전 확인하기

```java
az aks show --resource-group myResourceGroup --name myAKSCluster --output table
```

```java
Name          Location    ResourceGroup    KubernetesVersion    CurrentKubernetesVersion    ProvisioningState    Fqdn
------------  ----------  ---------------  -------------------  --------------------------  -------------------  ----------------------------------------------
myAKSCluster  eastus      myResourceGroup  1.28.11              1.28.11                     Upgrading            myakscluster-dns-jvy1fjgm.hcp.eastus.azmk8s.io
```

### 클러스터 삭제

- Azure 요금이 나가는것을 방지하기 위해 클러스터를 삭제하고 실습을 종료한다.

```java
az group delete --name myResourceGroup --yes --no-wait
```