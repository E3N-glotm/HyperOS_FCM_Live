# HyperOS FCM Live — English

**Language: [简体中文](README.md) | English (current)**


LSPosed compatibility fork for **HyperOS 4 / Android 17**, integrating upstream PR #30 for the `PowerKeeper 4.2.00` `GmsObserver.updateFrameworkGmsNetStatus(boolean)` API. Adds per-method optional Greeze hooking, renamed ListAppsManager field fallbacks, FCM-only broadcast exemption, and immutable whitelist safety.

Runtime hook registration was verified on Xiaomi `pudding` / `OS4.0.4.0.XPCCNXM` / Android 17 / LSPosed API 102. End-to-end message-delivery latency has **not** been independently verified.

The current v1.4.1 asset is a device-tested **debug-signed APK**, not a reproducibly signed production artifact. Future builds may have different signing certificates and require uninstall/reinstall rather than in-place upgrading. Never force an incompatible signature update.

The E3N package uses a separate application ID so it can coexist with the original signed module. **Keep the original module disabled** and enable this version in LSPosed with scopes **System Framework** and **com.miui.powerkeeper**, then reboot. Disable the fork and reboot to restore original behavior.

Original author: [Howard20181](https://github.com/Howard20181). HyperOS 4 GmsObserver adaptation credit: [793354162, upstream PR #30](https://github.com/Howard20181/HyperOS_FCM_Live/pull/30). This derivative remains licensed under GPL-3.0.
