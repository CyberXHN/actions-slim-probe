# actions-slim-probe

GitHub Actions `ubuntu-slim`（1 vCPU / 5 GB 容器型 runner）前置条件探针仓。

- 用途：验证私有主仓 CI 的**前置步骤**在 slim runner 上是否可行、耗时多少——`sudo apt-get install libgl1`（非特权容器关键卡点）、`setup-python` 3.10、三份 requirements + torch CPU + onnx 的安装耗时；不跑业务测试
- 公开仓 = 标准 runner 免费不限量，不占私有仓额度
- `requirements-*.txt` 为私有主仓对应文件的有效依赖行提取（纯 PyPI 公开包，无敏感信息）
- 数据判据：libgl1 装不上 = opencv import 前置死；「安装段耗时 + 测试段预算」须落在 15 分钟硬顶内
- 测完可整仓删除
