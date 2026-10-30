# SORTMARK Robot Arm Kinematics Simulator (7-DoF / 6-DoF)

<p align="center">
  <a href="#-english">English</a> | <a href="#-中文说明">简体中文</a> | <a href="#-日本語">日本語</a> | <a href="https://sortmark.com">Official Portal 官网</a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License" /></a>
  <a href="https://threejs.org/"><img src="https://img.shields.io/badge/Render-WebGL%20Three.js-cyan.svg" alt="WebGL" /></a>
  <a href="https://sortmark.com"><img src="https://img.shields.io/badge/Crafted%20by-SORTMARK-white.svg" alt="Brand" /></a>
</p>

---

## 🌐 English

An interactive, high-precision **7-Axis (Redundant) and 6-Axis (Industrial)** robotic arm kinematics and spatial motion simulator. Runs entirely in the browser with local system fonts and zero external network dependencies.

Crafted by the **[SORTMARK Lab Team](https://sortmark.com)**.

### 🌟 Key Features
* **Dual Kinematic Topologies**:
  * **7-DoF Redundant Manipulator**: Full 7-axis anthropomorphic dexterity with null-space elbow swivel optimization.
  * **6-DoF Industrial Arm**: Standard industrial arm mode with co-planar elbow constraint, demonstrating classical $SO(3) \times \mathbb{R}^3$ pose targeting.
* **Real-time Forward Kinematics (FK) Telemetry**:
  * Live Tool Center Point (TCP) spatial coordinates $(X, Y, Z)$ in millimeters and reach distance calculation.
  * Joint angle sliders ($J_1 \sim J_7$) with smooth hardware-accelerated WebGL response.
* **Actuator Internal Cutaway & Exploded Views**:
  * Concentric brushless torque motor + harmonic drive reduction principles.
  * Modular carbon-fiber composite tube-plate beams vs. classical dual-plate structures.
* **Local System Fonts & Air-Gapped Ready**:
  * Built using native open-source system font stacks for instant render without external font loading delays.

### 📐 Mathematical Formulation (Denavit-Hartenberg)
$$T_i^{i-1} = \begin{bmatrix}
\cos \theta_i & -\sin \theta_i \cos \alpha_i & \sin \theta_i \sin \alpha_i & a_i \cos \theta_i \\
\sin \theta_i & \cos \theta_i \cos \alpha_i & -\cos \theta_i \sin \alpha_i & a_i \sin \theta_i \\
0 & \sin \alpha_i & \cos \alpha_i & d_i \\
0 & 0 & 0 & 1
\end{bmatrix}$$

$$T_{TCP}^0 = \prod_{i=1}^{n} T_i^{i-1}$$

### 🚀 Quick Start
```bash
# Clone the repository
git clone https://github.com/sortmark-lab/robot-arm-kinematics.git
cd robot-arm-kinematics

# Start local preview
npx serve -l 3000 .
```
Open `http://localhost:3000` in your browser.

---

## 🇨🇳 中文说明

高精度交互式 **7 轴（冗余自由度）与 6 轴（标准工业臂）** 机器人空间运动学正向仿真平台。纯浏览器端独立运行，使用本地系统字体栈，零外部网络依赖与云端通信。

由 **[SORTMARK Lab Team](https://sortmark.com)** 研发打造。

### 🌟 核心特性
* **双拓扑运动学模式**:
  * **7 轴拟人冗余协作臂**: 具备全 7 自由度拟人灵巧度与零空间（Null-space）肘部绕轴旋转寻优避障特性。
  * **6 轴标准工业臂**: 经典工业机械臂构型，展示标准 $SO(3) \times \mathbb{R}^3$ 位姿到达约束。
* **实时正向运动学 (FK) 遥测**:
  * 实时末端工具中心点 (TCP) 空间坐标 $(X, Y, Z)$ 毫米级毫秒刷新与臂展距离计算。
  * 关节角滑块 ($J_1 \sim J_7$) 支持硬件加速 WebGL 顺滑渲染与联动。
* **一体化关节模组剖面与爆炸图**:
  * 同轴直驱无刷力矩电机 + 谐波减速机传动剖面。
  * 碳纤维轻量化管套梁与经典双侧板结构力学对比。
* **离线优先与工业控制级适应性**:
  * 纯系统级字体栈渲染，无需加载 Google Fonts 等外部 CDN，适用于离线隔离机房与工业控制台。

### 🚀 快速启动
```bash
git clone https://github.com/sortmark-lab/robot-arm-kinematics.git
cd robot-arm-kinematics
npx serve -l 3000 .
```

---

## 🇯🇵 日本語

高精度・対話型 **7軸（冗長自由度協働アーム）および 6軸（標準産業用アーム）** ロボットアームの順運動学（FK）および空間動作シミュレータ。外部ネットワークやWebフォントへの依存なく、ブラウザ環境にてオフラインで動作します。

開発: **[SORTMARK Lab Team](https://sortmark.com)**

### 🌟 主な機能
* **デュアル・キネマティクス・トポロジー**:
  * **7軸冗長協働アーム**: 人間のような柔軟性を持ち、零空間（Null-space）を活用した肘の姿勢最適化と障害物回避を再現。
  * **6軸産業用アーム**: 古典的な $SO(3) \times \mathbb{R}^3$ エンドエフェクタ姿勢制御と共面拘束を明示。
* **リアルタイム順運動学 (FK) テレメトリ**:
  * ツールセンターポイント (TCP) の空間3次元座標 $(X, Y, Z)$ [mm] およびリーチ距離をリアルタイム算出。
  * 関節角度スライダー ($J_1 \sim J_7$) によるハードウェアアクセラレーションWebGL描画。
* **アクチュエータ内部断面 & 軸方向分解ビュー**:
  * 同軸ブラシレストルクモータ＋波動歯車減速機（ハーモニックドライブ）の減速伝達原理。
  * 炭素繊維複合材チューブアームと従来型プレート構造の剛性・軽量性比較。
* **ローカルフォント・エアギャップ環境対応**:
  * 外部CDNフォントのダウンロード遅延を排除し、閉域網の産業用PCでも瞬時に高解像度レンダリング。

### 🚀 クイックスタート
```bash
git clone https://github.com/sortmark-lab/robot-arm-kinematics.git
cd robot-arm-kinematics
npx serve -l 3000 .
```

---

---

## 🔬 Project Status, Evaluation Disclaimer & Feedback / 项目状态、免责声明与反馈

### 🌐 English
> ⚠️ **Evaluation Prototype Notice (Not Intended for Critical or Production Control)**:  
> This open-source repository is an experimental educational and simulation preview under active development. It is provided strictly **"AS IS"** for educational inspection, kinematics/mechanics study, and technical evaluation. It is **not certified for physical safety-critical machinery, high-voltage industrial automation, or direct production deployment**. We make no commercial promises or operational warranties. We warmly welcome community feedback, pull requests, and suggestions to help us refine and improve!  
> 📬 *Community Contact & Feedback*: [`contact@sortmark.com`](mailto:contact@sortmark.com)

### 🇨🇳 简体中文
> ⚠️ **评估原型免责声明（仅用于技术验证与教育交流，不建议直接用于生产工控）**:  
> 本开源项目属于处于持续迭代完善中的实验性技术演示与评估原型，按“现状（AS IS）”提供。**仅供机构原理教学、算法仿真验证与离线学习参考，未经工业安全与关键任务控制认证，不建议也不承诺直接应用于物理实体机电设备或工业生产控制**。本团队不作任何商业承诺或可用性担保。热忱欢迎广大开发者、机器人与语言学爱好者提出宝贵的改进建议与 Issue 反馈！  
> 📬 *交流与反馈渠道*: [`contact@sortmark.com`](mailto:contact@sortmark.com)

### 🇯🇵 日本語
> ⚠️ **評価用プロトタイプに関する免責事項（教育・研究評価用・重要制御への投入非推奨）**:  
> 本オープンソースプロジェクトは、現在も継続的な改良を行っている実験的な教育・シミュレーション用プレビューです。機構原理の学習、アルゴリズムの動作検証、概念実証を目的として現状有姿（AS IS）で公開されており、**物理的な実機機械の保安制御や産業生産現場への直接投入は推奨しておらず、一切の商用保証を行いません**。機能向上や品質改善に向けたコミュニティからのご意見・改善提案・Issue報告を心より歓迎いたします！  
> 📬 *フィードバック窓口*: [`contact@sortmark.com`](mailto:contact@sortmark.com)

## 📄 License
Released under the [MIT License](LICENSE).
