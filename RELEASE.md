# 发布流程

## 发布前检查

- 确认 `package.json` 版本号正确
- 确认 `mineradio.update.owner/repo` 指向正式仓库
- 确认 `.cookie`、`.qq-cookie`、`updates/`、`node_modules/` 没有进入 git
- 运行语法检查
- 运行桌面应用进行基础功能验证
- 生成 Windows 安装包

## GitHub Release

Release tag 建议使用：

```text
v0.9.9
```

Release 标题建议使用：

```text
Mineradio v0.9.9
```

Release 资产建议上传 Windows 安装包，而不是 `win-unpacked` 目录。

## 更新检测

应用会请求 GitHub Releases latest。只有远端版本高于本地版本时，右上角更新入口才应显示真实更新内容。
