# 机械键盘 3D 拆解

单文件 Three.js 展示页。程序化建模一把机械键盘，支持拖动旋转、缩放、八层错峰拆解和复位，适合横屏与手机竖屏录屏。

## 本地打开

在本目录运行以下任一命令，然后访问 `http://localhost:8000/`：

```bash
python -m http.server 8000
```

也可使用 `python3 -m http.server 8000`。页面通过 importmap 从 `https://cdn.jsdelivr.net/npm/three@0.160.0/` 加载 Three.js 及同版本扩展，因此首次打开需要联网。请通过本地静态服务器访问；直接双击 `index.html` 可能因浏览器模块加载限制而无法运行。

## 操作

- 鼠标左键拖动或手机单指拖动：旋转键盘。
- 鼠标滚轮或手机双指：缩放。
- 点击「拆解」：八层依次散开，相机转到展示视角，标签逐层出现。
- 点击「复位」：标签淡出，零件反向合回，相机返回初始视角。

## 调整参数

所有可调参数集中在 `index.html` 顶部脚本的 `CONFIG` 对象：

- `layers` 的 `assembled`、`exploded`：各层组装与拆解后的 Y 位置；调整 `exploded` 改变层间距。
- `motion`：`stagger` 为层间启动间隔（毫秒），`duration`、`resetDuration` 为单层时长，`back` 为拆解末尾回弹力度，`cameraDuration` 为镜头移动时长。
- `cameras.wide`、`cameras.tall`：横屏与竖屏的初始和展示机位，各有 `position`、`target` 和 `fov`。
- `colors`：主要零件与地面的颜色。材质的金属度和粗糙度可在脚本的 `M` 对象中调节。

项目无打包步骤、后端、外部模型或图片资源。
