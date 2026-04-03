# MEMORY.md - 长期记忆

## 用户项目
正在构建一套「短视频文案编写技能框架」，适用于全域短视频平台。每个框架产出：说明文档 + Prompt模板。

## 框架存储位置
`C:\Users\EDY\.workbuddy\skills\writing-frameworks\frames\`

## 框架一（已完成）：原子信息喂养 FR-001

### 核心结构
大框架：开头hook → 原子1 → 原子2 → ... → 原子N → [收尾]
小框架：可作为内嵌技法，在其他框架的段落中填充信息密度

### 核心原则
陌生感 ↔ 熟悉感交替
- 陌生感来源：学说引用、反常识观点、新概念
- 熟悉感来源：具象场景、常见痛点、观众经历

### 三大配套技法
1. **抽象接具象**：抽象结论 + 具象例子，直接拼接
2. **引用学说/名言/真理**：权威理论背书观点
3. **观点陌生熟悉化**：
   - 创造/借用新词（斩杀线、祛魅、情绪劳动……）
   - 蹭热度
   - 反常识颠覆

## 用户偏好
- 不要说"好的"、不要"我来帮你"等套话
- 直接行动
- 风格偏实战、偏深度
- 例子要具体可感，避免太常见的信息
- 学术引用要深入（未来要求）

## Git 同步仓库

**地址**：`https://github.com/RichJaron/writing-frameworks`

**同步内容**：
- `skills/writing-frameworks/` — 框架 + Prompt + 示例
- `memory/MEMORY.md` — 判断标准 + 用户偏好

**克隆目标路径**：`C:\Users\EDY\.workbuddy\`
- skills 路径天然对齐
- memory/MEMORY.md 直接放进该路径，WorkBuddy 可读取

**更新命令**：
```powershell
cd C:\Users\EDY\.workbuddy
git add skills/writing-frameworks memory/MEMORY.md
git commit -m "update: ..."
git push
```

## 进行中任务
- 继续构建下一个框架（用户将提供）
