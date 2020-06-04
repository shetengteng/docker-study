# Pod

| 命令                                                         | 描述                                           | 备注                 |
| ------------------------------------------------------------ | ---------------------------------------------- | -------------------- |
| kubectl get po -a                                            | 查看已完成的pod                                | -a 等价于 --show-all |
| kubectl delete po --all                                      | 删除所有的pod                                  | --all                |
| kubectl get pods --show-labels -n NAMESPACE                  | 查看指定namespace的pods的信息，包含所有的label |                      |
| kubectl delete pod podName -n NAMESPACE --force --grace-period=0 | 强制删除                                       |                      |



# Label

- 给目标打上标签，用于过滤依据使用

| 命令                                                         | 描述               | 备注   |
| ------------------------------------------------------------ | ------------------ | ------ |
| kubectl label node NODE_NAME LABEL_NAME=LABEL_VALUE          | 给node添加标签与值 | create |
| kubectl label node NODE_NAME LABEL_NAME=LABEL_VALUE --overwrite | 更新node的标签与值 | update |
|                                                              |                    |        |



# ReplicationController

| 命令                                      | 描述                                                     | 备注 |
| ----------------------------------------- | -------------------------------------------------------- | ---- |
| kubectl delete rc RC_NAME --cascade=false | 删除指定的ReplicationController，但不删除该rc下管理的pod |      |
|                                           |                                                          |      |
|                                           |                                                          |      |



# ReplicaSet

- ReplicationController的替代品
-  提供更丰富的label过滤

| 命令                                        | 描述                     | 备注                      |
| ------------------------------------------- | ------------------------ | ------------------------- |
| kubectl get rs                              | 查看所有的ReplicaSet     |                           |
| kubectl describe rs REPLICASET -n NAMESPACE | 查看某个ReplicaSet的描述 |                           |
| kubectl delete rs REPLICASET_NAME           | 删除指定的ReplicaSet     | 会删除该rs下管理的所有pod |
|                                             |                          |                           |
|                                             |                          |                           |



# DaemonSet

- 用于控制在每个node上运行一个pod

| 命令                                      | 描述                           | 备注 |
| ----------------------------------------- | ------------------------------ | ---- |
| kubectl get ds -A                         | 查看所有namespace中的daemonSet |      |
| kubectl describe ds  DS_NAME -n NAMESPACE | 查看该daemonSet的详细          |      |
|                                           |                                |      |
|                                           |                                |      |



# Job

- 用于临时任务的pod，pod正常执行完就关闭

| 命令             | 描述    | 备注 |
| ---------------- | ------- | ---- |
| kubectl get jobs | 查看job |      |
|                  |         |      |
|                  |         |      |
|                  |         |      |



# Service

- 给指定label的pods建立统一的ip访问服务

| 命令                           | 描述        | 备注 |
| ------------------------------ | ----------- | ---- |
| kubectl get svc -n kube-system | 查看service |      |
|                                |             |      |
|                                |             |      |



# Node

| 命令                              | 描述               | 备注 |
| --------------------------------- | ------------------ | ---- |
| kubectl get nodes                 | 查看nodes信息      |      |
| kubectl describe node <node_name> | 查看node的详细信息 |      |
|                                   |                    |      |



# Top

| 命令                                              | 描述              | 备注 |
| ------------------------------------------------- | ----------------- | ---- |
| kubectl top node \| grep xxx                      | 查看node的top信息 |      |
| kubectl top pod [pod_name] -n websrv --containers | 查看pod的top信息  |      |
|                                                   |                   |      |
|                                                   |                   |      |
|                                                   |                   |      |
|                                                   |                   |      |



# Exec

 kubectl exec -n demo -it nginx-busybox -c busybox -- sh

