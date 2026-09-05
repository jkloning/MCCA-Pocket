# MCCA-android

交错战线（CrossCore）MaaFramework 安卓迁移资源包。由 Windows 版 MCCA v1.7.5 迁移而来，通过 [MaaFwApp](https://github.com/Aliothmoon/MaaFwApp) 打包为安卓 APK（`com.aliothmoon.maafw.mcca`）。

## 迁移内容

- **流水线语法**：官方 [migrate_pipeline_v5.py](https://github.com/MaaXYZ/MaaFramework/blob/main/tools/migrate_pipeline_v5.py) 将 `is_sub`/`interrupt` 迁移至 v5.1 `[JumpBack]` 语法（适配 MaaFramework 5.12.3）
- **interface.json**：升级为 PI V2 清单（任务与选项在 `tasks/MCCA.json`，16 个选项全部补 `type` 字段：Yes/No → `switch`，单选 → `select`）
- **购物流水线**：`每日免费礼包.json` / `限时贸易.json` 按国服现行 UI 重制（模板 `shop_buy_btn.png`、`shop_free_tag.png`、`shop_trade_entry.png` 等取自实机截图）

## 打包

```bash
# MaaFwApp local.properties:
#   pi.profile=<本仓库外>/pi-profile-mcca.yaml
#   build.versionName=1.7.5
cd MaaFwApp && gradlew assembleDebug
# 产物: app/build/outputs/apk/debug/app-debug.apk
```

打包配方要点（`pi-profile-mcca.yaml`，仓库外）：

```yaml
assets: <本仓库路径>
include: [interface.json, tasks/**, resource/**, icon.png]
exclude: ['**/*.bak']
app: { id: mcca, label: MCCA, icon: <本仓库路径>/icon.png }
```

## 运行要求

- MaaFwApp 宿主 + Shizuku/root 授权
- **亮屏解锁**状态下运行（游戏锁屏会被冻结，任务将超时）
- USB 供电建议配合 `adb shell svc power stayon true`

## 已知限制

- `活动` 任务入口为固定区域盲点，活动更替后入口漂移即失效（上游已知问题）
- 消费类任务（限时贸易所购买）谨慎勾选：购买确认按模板锚定，但商品白名单为旧版文案
- 资源按 1280×720 设计，20:9 设备若游戏不 letterbox 则 ROI 错位

## 许可

迁移自 [MaaXYZ/MCCA](https://github.com/MaaXYZ/MCCA)（其资源许可继承上游）；打包宿主 MaaFwApp 为 AGPL-3.0。
