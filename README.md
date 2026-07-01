# Event_Report PLC Project

TIA Portal V21 工程，用于 S7-1215C PLC。

## 硬件

- CPU: 6ES7 215-1BG40-0XB0 / V4.2
- IP: `192.168.1.8`
- PROFINET 设备名: `haku-plc`

## 主要功能

1. **动态 DB → IO 映射**
   - `FB_MapDBtoIO` + `IDB_MapDBtoIO`
   - 默认将 `DB10.DBB0~5` 映射到 `I2.0~I7.7`
   - 参数在 `IDB_MapDBtoIO` 实例 DB 中在线配置

2. **输入采集与 UDP 上报**
   - `Main` 读取 `I0~I7` 到 `DB_InputMonitor.InputImage`
   - 变化检测后打包 100 字节到 `DB_CommData.SendBuffer`
   - `FB_UdpTx` 通过 UDP 发送到 `192.168.1.201:11451`

## 版本控制

工程文件使用 Git + GitHub 管理。

```bash
git add -A
git commit -m "描述变更"
git push origin main
```

注意：`Event_Report.ap21` 是二进制文件，`git diff` 不可读，提交主要用于快照备份。
