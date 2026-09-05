<div align="center">

<img src="icon.png" alt="MCCA Pocket" width="180">

# MCCA Pocket

_交错战线 · 安卓端 MaaFramework 助手_

基于图像识别的一键日常 · 手机原生运行

[![Release](https://img.shields.io/github/v/release/jkloning/MCCA-Pocket?style=flat-square)](https://github.com/jkloning/MCCA-Pocket/releases/latest)
[![License](https://img.shields.io/badge/license-继承上游-blue?style=flat-square)](#许可证)
[![MaaFramework](https://img.shields.io/badge/MaaFramework-5.12.3-green?style=flat-square)](https://github.com/MaaXYZ/MaaFramework)
[![Platform](https://img.shields.io/badge/platform-Android%20arm64--v8a-orange?style=flat-square)](运行要求)

[下载最新版](https://github.com/jkloning/MCCA-Pocket/releases/latest) · [问题反馈](https://github.com/jkloning/MCCA-Pocket/issues) · [上游 MCCA](https://github.com/MaaXYZ/MCCA)

</div>

> [!WARNING]
> 项目处于活跃开发与实测阶段，接口与任务行为可能随版本更新变动。游戏更新导致界面变化时，任务可能需要等待适配。

## 特性

| | 特性 | 说明 |
| --- | --- | --- |
| 📱 | 安卓原生 | 基于 MaaFwApp 宿主 + AndroidNative 控制器，无需连接电脑 |
| 🔑 | 权限方案 | Shizuku / Root 均可，无需解锁 Bootloader |
| 🤖 | 纯声明式流水线 | 全部任务为 MaaFramework v5.1 流水线，无 Python 依赖 |
| 🧭 | 自适应启动 | 兼容任意初始状态（登录页 / 公告 / 主界面）进入日常流程 |
| 🛡️ | 消费防护 | 购买类操作模板锚定确认按钮，限时贸易所保留商品白名单 |
| ⏱️ | 定时执行 | 由 MaaFwApp 宿主提供定时计划任务能力 |

## 任务列表

| 任务 | 状态 | 说明 |
| --- | --- | --- |
| 启动游戏 | ✅ 实测通过 | 冷启动 / 热启动均可，含公告关闭与签到 |
| 每日免费礼包 | ✅ 实测通过 | 主界面 → 补给站 → 礼包 → 免费礼包购买 |
| 限时贸易所购买 | ⚠️ 谨慎 | 商品白名单为旧版文案，购买前请自行确认 |
| 模拟军演 | ✅ 逻辑修复 | 对手战力 ≥ 阈值自动刷新（默认 <5000 才挑战） |
| 基建 | ✅ 已实测 | 好友访问与订单换取 |
| 每日探索 | ✅ 已实测 | 支持关卡 / 层数 / 次数选项 |
| 周本 | ✅ 已实测 | — |
| 领取奖励 | ✅ 实测通过 | 邮箱 + 每日 + 通行证 |
| 活动 | ❌ 不建议 | 活动入口随版本漂移，固定区域盲点（上游已知问题） |

## 运行要求

| 项目 | 要求 |
| --- | --- |
| 系统 | Android 9.0（API 28）及以上 |
| 权限 | Shizuku 或 Root（二者其一） |
| 架构 | arm64-v8a |
| 运行条件 | **亮屏解锁状态**（游戏在锁屏下会被冻结导致任务超时） |
| 分辨率 | 资源按 1280×720 设计，20:9 全面屏若游戏不 letterbox 则可能错位 |

## 安装

1. 从 [Releases](https://github.com/jkloning/MCCA-Pocket/releases/latest) 下载 APK
2. 安装并打开，按提示启动 Shizuku 并授权（Root 设备可选 Root 模式）
3. 选择服务器（官服 / B 服），勾选任务，开始

> [!TIP]
> 建议插电运行并开启系统的"屏幕常亮"，或通过 `adb shell svc power stayon true` 设置充电时常亮。

## 文档

| 文档 | 说明 |
| --- | --- |
| [上游 MCCA](https://github.com/MaaXYZ/MCCA) | Windows 版原项目，本仓库资源迁移自 v1.7.5 |
| [MaaFramework](https://github.com/MaaXYZ/MaaFramework) | 自动化框架（v5.12.3，v5.1 流水线语法） |
| [MaaFwApp](https://github.com/Aliothmoon/MaaFwApp) | 安卓打包宿主（AGPL-3.0） |
| [流水线迁移脚本](https://github.com/MaaXYZ/MaaFramework/blob/main/tools/migrate_pipeline_v5.py) | is_sub/interrupt → [JumpBack] 无损转换 |

## 与上游的差异

- 流水线全部迁移至 v5.1 语法（`[JumpBack]`），适配 MaaFramework 5.12.3
- interface.json 升级为 PI V2 清单结构（`tasks/MCCA.json`），16 个选项补全 `type` 字段
- 商店类流水线按现行国服客户端实截重制（模板取自实机截图）
- 主界面判定、军演刷新阈值正则等针对当前客户端修正

## 参与贡献

1. Fork 本仓库并创建分支
2. 修改 `resource/` 下的流水线与模板（模板请从实机截图裁剪）
3. 提交遵循 Conventional Commits（如 `fix: ...`、`feat: ...`）
4. 发起 Pull Request

## 致谢

- [MaaXYZ/MCCA](https://github.com/MaaXYZ/MCCA) —— 交错战线 Windows 助手，本仓库的资源来源
- [MaaXYZ/MaaFramework](https://github.com/MaaXYZ/MaaFramework) —— 自动化框架
- [Aliothmoon/MaaFwApp](https://github.com/Aliothmoon/MaaFwApp) —— 安卓打包宿主
- [Shizuku](https://github.com/RikkaApps/Shizuku) —— 特权 API 方案

## 许可证

本仓库资源迁移自 MCCA，许可证继承上游；MaaFwApp 宿主为 AGPL-3.0。第三方代码保留其原始许可证。
