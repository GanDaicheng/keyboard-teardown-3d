# 机械键盘 3D 拆解

单文件 Three.js 展示页。程序化建模一把机械键盘，支持拖动旋转、缩放、八层错峰拆解和复位。拆解时使用侧边标签与实时跟随的引线，适合横屏与手机竖屏录屏。

## 本地打开

在本目录运行以下任一命令，然后访问 `http://localhost:8000/`：

```bash
python -m http.server 8000
```

也可使用 `python3 -m http.server 8000`。页面通过 importmap 从 `https://cdn.jsdelivr.net/npm/three@0.160.0/` 加载 Three.js 及同版本扩展，因此首次打开需要联网。请通过本地静态服务器访问；直接双击 `index.html` 可能因浏览器模块加载限制而无法运行。

## 操作

- 鼠标左键拖动或手机单指拖动：旋转键盘。
- 鼠标滚轮或手机双指：缩放。
- 点击「拆解」：八层依次散开，相机转到展示视角，侧边标签和引线逐层出现。
- 点击「复位」：标签淡出，零件反向合回，相机返回初始视角。

## 调整参数

所有可调参数集中在 `index.html` 顶部脚本的 `CONFIG` 对象：

- `layers` 的 `assembled`、`exploded`：各层组装与拆解后的 Y 位置；`offsetZ` 是拆解时沿 Z 轴的额外偏移，空格键向前、USB 接口向后。USB 的 `offsetZ.wide/tall` 和 `offsetX.wide/tall` 分别控制横竖屏的前后与侧向位移，`turnY` 控制它在展示时转向镜头，避免被板层挡住。
- `motion`：`stagger` 为层间启动间隔（毫秒），`duration`、`resetDuration` 为单层时长，`back` 为拆解末尾回弹力度，`cameraDuration` 为镜头移动时长。
- `cameras.wide`、`cameras.tall`：横屏与竖屏的初始和展示机位，各有 `position`、`target` 和 `fov`。
- `leaders`：引线宽度、透明度、锚点半径、标签间距与位置；`anchors` 是八层各自的局部坐标锚点，`labelYShift` 可微调个别标签的高度。
- `keyLegends`：按键字符列表；字符用代码生成的 CanvasTexture 绘制，未加载外部字体或图片。
- `colors`：主要零件、红轴轴心、字符和地面的颜色；`background` 控制蓝灰网格和冷光背景。材质的金属度和粗糙度可在脚本的 `M` 对象中调节。

项目无打包步骤、后端、外部模型或图片资源。
