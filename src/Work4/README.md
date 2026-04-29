# Work4: Phong Shading Demo (Taichi Ray Tracing)

这是一个基于 **Taichi Lang** 实现的光线追踪（Ray Tracing）演示项目，重点展示了 **Phong 光照模型** 在 3D 几何体（球体和圆锥）上的应用效果。

## 效果演示

![光线追踪演示](https://github.com/lydia520520/cg-lab/blob/main/assets/Work4.gif)
(如长时间未加载出gif 可查看assets/Work4.gif)

## 项目简介

该项目在 GPU 上并行运行，通过模拟光线从摄像机射出并与场景中的几何体相交，计算交点处的光照颜色。它包含了一个红色球体和一个紫色圆锥，并提供了一个交互式 GUI 面板来实时调整材质参数。

## 主要特性

- **Phong 光照模型实现**：包含环境光（Ambient）、漫反射（Diffuse）和镜面反射（Specular）三个分量。
- **几何体求交算法**：
  - 球体（Sphere）求交与法线计算。
  - 竖直圆锥（Cone）求交与解析法线计算。
- **实时交互**：通过 Taichi GGUI 提供的滑块，可以实时修改材质参数。
- **高性能渲染**：利用 Taichi 的 GPU 加速能力，实现流畅的实时渲染。

## 运行环境

- **操作系统**: Windows / Linux / macOS
- **包管理工具**: [uv](https://github.com/astral-sh/uv)
- **主要依赖**: `taichi`

## 如何运行

请确保你已安装 `uv`，然后在项目根目录（`c:\code\CG-lab`）下执行：

```powershell
uv run src/Work4/main.py
```

如果是首次运行，建议先同步依赖：
```powershell
uv sync
```

## 代码参考

- [main.py](file:///c:/code/CG-lab/src/Work4/main.py): 项目核心代码，包含渲染管线和 GUI 逻辑。
- `intersect_sphere`: [main.py:L27](file:///c:/code/CG-lab/src/Work4/main.py#L27) - 球体求交函数。
- `intersect_cone`: [main.py:L44](file:///c:/code/CG-lab/src/Work4/main.py#L44) - 圆锥求交函数。
- `render`: [main.py:L93](file:///c:/code/CG-lab/src/Work4/main.py#L93) - 并行渲染内核。

## 交互指南

程序启动后，右侧会显示 **Material Parameters** 面板：
1. **Ka (Ambient)**: 调整物体在阴影处的亮度。
2. **Kd (Diffuse)**: 调整物体的固有颜色亮度和质感。
3. **Ks (Specular)**: 调整高光亮点强度。
4. **N (Shininess)**: 调整高光的集中程度（值越大，高光点越小越尖锐）。
