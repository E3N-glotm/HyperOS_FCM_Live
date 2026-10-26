# HyperOS FCM Live · HyperOS 4 FCM 推送兼容修复

**语言：简体中文（当前） | [English](README_EN.md)**

基于 [Howard20181/HyperOS_FCM_Live](https://github.com/Howard20181/HyperOS_FCM_Live) 的 LSPosed 兼容分支，面向 HyperOS 4 / Android 17 上 Google FCM 广播、PowerKeeper 和 Greeze API 变化。遵循原项目 GPL-3.0 协议。

**E3N 版本：v1.4.1** · [下载 Release](https://github.com/E3N-glotm/HyperOS_FCM_Live/releases) · [提交上游的兼容修复 PR](https://github.com/Howard20181/HyperOS_FCM_Live/pull/31)

## 修复内容

- 在系统实现发生变化时，独立探测 Greeze Hook 方法与 ListAppsManager 字段，缺失的旧接口安全跳过。
- 兼容 HyperOS 4 的 `GmsObserver.updateFrameworkGmsNetStatus(boolean)`。
- 对 `DomesticPolicyManager.deferBroadcast` **只放行与 FCM 相关的广播**，不关闭无关应用的全部延迟广播机制。
- 避免修改不可变白名单导致异常；记录实际 Hook 注册信息供 LSPosed 排错。

## 实机验证

曾在 Xiaomi `pudding`、`OS4.0.4.0.XPCCNXM`、Android 17、PowerKeeper `4.2.00`、LSPosed `2.2.1/API 102` 上确认 Hook 注册、冷启动无相关崩溃，GMS `GcmService` 有效连接。**这不等于已单独完成数小时锁屏的端到端微信消息延迟测试**。

## 安装与使用

1. 从 [Releases](https://github.com/E3N-glotm/HyperOS_FCM_Live/releases) 下载 APK。
2. 安装后，在 LSPosed 启用本 Fork，作用域选择 **系统框架** 和 **PowerKeeper（`com.miui.powerkeeper`）**，再重启。
3. 使用独立包名 `io.github.e3n.hyperos.fcmlive`。**不要与上游原版同时启用**，否则可能重复 Hook。
4. 异常时先停用本模块并重启；必要时使用 LSPosed 安全模式恢复。

> 当前附件为实机验证的 **Debug 签名 APK**。未来不同构建证书可能不匹配，不能保证直接覆盖升级。不要强制覆盖签名不一致的 APK；更换时需要先备份作用域与配置。

## 限制

可能增加后台唤醒与耗电；不替代 Google Play 服务本身的联网、Token 注册或 Millet Guard 的管理。对其他 HyperOS 版本采用实际接口匹配，未经实机验证的组合仍有兼容风险。具体差异与原作者致谢见 [兼容性说明](docs/HYPEROS4_COMPAT.md)。
