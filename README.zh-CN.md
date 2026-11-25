# Color Study Lab 🎨｜色感训练器

**练习HSB拾色**

[English README](README.md) · [中文版首页](zh/index.html) · [English Home](en/index.html)

三种模式：HSB色感训练/明度训练/上传照片色块训练
旨在提高对颜色的辨识度，为系统性色彩训练打下基础。从零开始的色彩训练之旅，如果做V大预科都有困难，不如先从拾色开始训练。

## 在线 / 本地运行

- **[HSB 色彩训练](zh/apps/hsb-trainer.html)**：单/双色模式；可自选HSB评分权重及算法。
- **[黑白灰明度训练](zh/apps/value-trainer.html)**：上传图片或使用示例，将图片压缩成 **2–12 个明度阶**，逐阶猜测明度并查看误差。
- **[照片色彩归纳训练](zh/apps/photo-color-study.html)**：上传图片，归纳成 **2–12 组颜色**，点击分区通过 HSB 滑块填色并评分。

下载仓库后，在浏览器中打开 `index.html`

## 评分算法

四种评分算法可选：

1. **RGB K-Means**：在 RGB 空间聚类，使用簇平均色。
2. **OKLab K-Means**：根据肉眼对颜色的感知，进行相似度评分。
3. **原图代表色**：在 OKLab 聚类后，选择接近簇中心的实际采样色。
4. **鲜艳优先**：增加高彩度像素的聚类权重，并从原图采样代表色。

算法按照颜色相似性聚类，**不具备语义分割能力**。对于色彩丰富的复杂插画，可能产生零碎色块或丢失细节。

## 结构

```text
color-study-lab/
├── index.html               # 语言选择页
├── README.md                # English documentation
├── README.zh-CN.md          # 中文项目说明
├── zh/
│   ├── index.html           # 中文首页
│   └── apps/
│       ├── hsb-trainer.html
│       ├── value-trainer.html
│       └── photo-color-study.html
└── en/
    ├── index.html           # English homepage
    └── apps/
        ├── hsb-trainer.html
        ├── value-trainer.html
        └── photo-color-study.html
```

三个模块均为独立 HTML 文件，包含各自的 HTML、CSS 和 JavaScript。中英文界面分别维护，提供相同的核心功能。

## GitHub Pages 部署

进入仓库 **Settings → Pages**，选择 **Deploy from a branch**，将默认分支的 `/(root)` 目录设为发布目录。根目录首页会先显示中文和英文入口，两个语言版本内部都可以切换语言。

## 技术说明

- **HSB / HSV**：滑块使用的色彩模型，B 不等于人眼感知明度。
- **OKLab**：用于感知色差比较；将距离映射到 0–100 分的方式是项目自定义的练习评分，不是标准化测评。
- **黑白灰模块**：使用 sRGB 加权灰度，不是 CIELAB L*。
- **照片归纳模块**：基于 K-Means 类算法，不理解物体结构或画面的光照逻辑。
- **图片隐私**：图片全程本地浏览器处理，不上传云端服务器，更不会用于AI训练！！！

## 后续计划

- [ ] 改善移动端操作体验
- [ ] 优化复杂插画的色彩归纳效果
- [ ] 添加训练记录功能
- [ ] 探索每日挑战与分享功能

## License

MIT License
