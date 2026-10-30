# 机械臂运动学仿真原理与模型说明 (Kinematics Principles & Model Architecture)

> **归属实验室**: SORTMARK Open-Source Lab (`sortmark-opensource-lab`)  
> **所属项目**: `robot-arm-kinematics`  
> **官方主页**: [https://sortmark.com](https://sortmark.com) | **商务咨询**: `contact@sortmark.com`

---

## 📌 1. 核心设计原则：纯 HTML 仿真，零外部 3D 模型依赖

本项目是纯正的**工业机械臂运动学原理演示平台**，**不提供、亦不依赖任何外部 3D CAD/GLB 二进制模型文件**：

1. **商业 IP 安全保护**:
   - 生产级 6 轴与 7 轴机械臂的 STEP 图纸、轴承公差与减速箱装配体属于核心工程资产，不作为免费开源资产公开。
2. **纯 HTML 原理仿真 (Zero-Dependency Procedural Simulation)**:
   - 全部关节（Base、J1 ~ J7、法兰、TCP 坐标轴）均在前端通过 Three.js 原生参数化数学几何体矩阵实时计算生成。
   - 体积仅数十 KB，用户打开 `index.html` 3 秒内即可直观交互，无任何外部大文件下载阻塞。
3. **商业定制渠道**:
   - 实体机械臂采购、高精度制造 CAD 工程图纸、ROS 2 MoveIt 闭环驱动及定制控制系统，请通过商务渠道联系 `contact@sortmark.com`。

---

## 🏭 2. AI 模型生产流水线：`model-builder` 与 `model-factory`

若需要为空间机械臂交互引入 AI 自然语言控制与参数推理智能体，模型处理统一遵循工作区标准流水线，无需在前端手写模型逻辑：

1. **模型微调与量化工序**:
   - 车间路径：`sortmark/sortmark-model-builder`
   - 使用 LLaMA-Factory 对开源基座（Qwen2.5-3B-Instruct）进行空间计算与指令映射微调，导出标准 GGUF 量化文件（Q4_K_M）。
2. **Hugging Face 矩阵发布与高权外链**:
   - 车间路径：`social_matrix/custom-model-factory`
   - 自动生成符合规范的官方 Model Card（如 `sortmark/spatial-docent-3d-agent-gguf`），通过 API 发布至 Hugging Face，为 `https://sortmark.com` 建立权威反向链接。
