# dockerized-tcf

本仓库着眼于为[hyperledger-labs/trusted-compute-framework](https://github.com/hyperledger-labs/trusted-compute-framework)项目添加基于kubernetes的开发环境搭建方式。

## 前期软件准备
- kubectl-v1.15.2
- 配置kubernetes集群

## 搭建环境

1. 启动LMDB服务器
    ```bash
    # 启动相应的Pod和Serivice
    kubectl create -f lmdb.yaml
    ```
2. 启动`EnclaveManager`（用于管理SGX enclave）和`TCSServer`（负责监听并处理客户端请求）
    ```bash
    kubectl create -f enclave-manager-deployment.yaml

    kubectl create -f tcs.yaml
    ```

## 使用示例
1. 发送工单请求
    ```bash
    kubectl create -f propose-requests-job.yaml
    ```

2. 查看请求处理过程的日志
    ```bash
    # 假设 propose-request-abcde 是上一步创建的 job
    kubectl logs propose-request-abcde

    # 即可得到部分输出如下
    [23:20:36 INFO    __main__] Signature Verified
    [23:20:36 INFO    utility.utility] Decryption Result at Client - You have a risk of 71% to have heart disease. 
    ```
