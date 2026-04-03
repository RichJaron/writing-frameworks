# Git同步指南 - 文案框架技能库

## 仓库信息
- **仓库地址**：`https://github.com/RichJaron/writing-frameworks`
- **仓库结构**：修复后的正确结构（已推送）
- **最后一次提交**：`refactor: restructure to fix nested skills directory`

## 🚀 如何在另一台计算机上安装

### 方法一：标准安装（推荐）

1. **克隆仓库**：
   ```bash
   # 克隆到WorkBuddy技能目录
   cd ~/.workbuddy/skills
   git clone https://github.com/RichJaron/writing-frameworks
   ```

2. **自动修复结构**：
   ```bash
   cd writing-frameworks
   
   # 检查是否需要修复结构（如果克隆后有skills/目录）
   if [ -d "skills/writing-frameworks/frames" ]; then
     echo "检测到嵌套结构，正在修复..."
     mv skills/writing-frameworks/frames/ frames/
     rm -rf skills/
     echo "修复完成！"
   fi
   ```

3. **更新MEMORY.md中的用户路径**：
   ```bash
   # 编辑MEMORY.md，将路径改为当前用户名
   sed -i "s/C:\\Users\\EDY/C:\\Users\\$USERNAME/g" memory/MEMORY.md
   sed -i "s/C:\\Users\\HUAWEI/C:\\Users\\$USERNAME/g" memory/MEMORY.md
   ```

### 方法二：手动安装

1. **克隆到临时位置**：
   ```bash
   git clone https://github.com/RichJaron/writing-frameworks /tmp/writing-frameworks
   ```

2. **复制到正确位置**：
   ```bash
   # 复制到WorkBuddy技能目录
   cp -r /tmp/writing-frameworks ~/.workbuddy/skills/
   ```

3. **调整结构**：
   ```bash
   cd ~/.workbuddy/skills/writing-frameworks
   
   # 如果存在嵌套结构
   if [ -d "skills/writing-frameworks" ]; then
     mv skills/writing-frameworks/frames/ ./
     mv skills/writing-frameworks/memory/ ./
     mv skills/writing-frameworks/SKILL.md ./
     rm -rf skills/
   fi
   ```

### 方法三：使用同步脚本

创建一个安装脚本 `install-writing-frameworks.sh`：
```bash
#!/bin/bash

REPO_URL="https://github.com/RichJaron/writing-frameworks"
TARGET_DIR="$HOME/.workbuddy/skills/writing-frameworks"

echo "安装文案框架技能库..."

# 克隆或更新
if [ -d "$TARGET_DIR" ]; then
    echo "技能库已存在，更新中..."
    cd "$TARGET_DIR"
    git pull
else
    echo "克隆仓库..."
    cd ~/.workbuddy/skills
    git clone $REPO_URL
fi

# 修复结构
cd "$TARGET_DIR"
if [ -d "skills/writing-frameworks" ]; then
    echo "修复目录结构..."
    mv skills/writing-frameworks/frames/ ./
    mv skills/writing-frameworks/memory/ ./
    mv skills/writing-frameworks/SKILL.md ./
    rm -rf skills/
fi

# 更新用户路径
echo "更新用户路径..."
CURRENT_USER=$(whoami)
if [[ "$OSTYPE" == "darwin"* ]]; then
    # macOS
    sed -i '' "s/C:\\Users\\EDY/\/Users\/$CURRENT_USER/g" memory/MEMORY.md
    sed -i '' "s/C:\\Users\\HUAWEI/\/Users\/$CURRENT_USER/g" memory/MEMORY.md
elif [[ "$OSTYPE" == "linux-gnu"* ]]; then
    # Linux
    sed -i "s/C:\\Users\\EDY/\/home\/$CURRENT_USER/g" memory/MEMORY.md
    sed -i "s/C:\\Users\\HUAWEI/\/home\/$CURRENT_USER/g" memory/MEMORY.md
else
    # Windows
    sed -i "s/C:\\Users\\EDY/C:\\Users\\$CURRENT_USER/g" memory/MEMORY.md
    sed -i "s/C:\\Users\\HUAWEI/C:\\Users\\$CURRENT_USER/g" memory/MEMORY.md
fi

echo "✅ 安装完成！技能库已准备就绪。"
```

## 🔄 日常更新工作流

### 本地更新后推送到远程
```bash
# 在你的计算机上
cd ~/.workbuddy/skills/writing-frameworks

# 查看状态
git status

# 添加变更
git add .

# 提交
git commit -m "更新：描述你的变更"

# 推送
git push
```

### 其他计算机拉取更新
```bash
# 在其他计算机上
cd ~/.workbuddy/skills/writing-frameworks

# 拉取最新变更
git pull

# 如果结构有变化，可能需要手动调整
if [ -d "skills/writing-frameworks" ]; then
    echo "检测到结构变化，正在修复..."
    mv skills/writing-frameworks/frames/ ./
    rm -rf skills/
fi
```

## 🛠️ 故障排除

### 问题1：Git推送被拒绝
```bash
# 先拉取最新变更
git pull --rebase

# 如果有冲突，解决冲突后
git add .
git rebase --continue

# 再次推送
git push
```

### 问题2：结构混乱
```bash
# 重置到最新状态
cd ~/.workbuddy/skills/writing-frameworks
git fetch origin
git reset --hard origin/main

# 重新修复结构
if [ -d "skills/writing-frameworks" ]; then
    mv skills/writing-frameworks/frames/ ./
    rm -rf skills/
fi
```

### 问题3：WorkBuddy无法识别技能
```bash
# 检查SKILL.md文件
cat SKILL.md

# 确保name字段正确
# name: writing-frameworks

# 重启WorkBuddy或重新加载技能
```

## 📁 当前仓库结构（已修复）

```
writing-frameworks/
├── .gitignore
├── SYNC_GUIDE.md          # 本文件
├── SKILL.md              # 技能主文档
├── frames/               # 框架目录
│   └── FR-001-atom-info/
│       ├── README.md    # 框架详细说明
│       ├── prompt.md    # Prompt模板
│       └── examples/    # 市场验证案例
└── memory/
    └── MEMORY.md        # 用户偏好和项目信息
```

## 📝 注意事项

1. **用户路径**：`MEMORY.md`中包含用户特定的路径，需要在每台计算机上更新
2. **Git用户信息**：建议配置Git用户信息
   ```bash
   git config user.email "your-email@example.com"
   git config user.name "Your Name"
   ```
3. **权限问题**：确保有推送权限到GitHub仓库
4. **备份**：重要变更前建议备份本地副本

## 🎯 快速检查清单

- [ ] 克隆仓库到正确位置
- [ ] 修复嵌套的`skills/`目录（如果需要）
- [ ] 更新`MEMORY.md`中的用户路径
- [ ] 重启WorkBuddy或重新加载技能
- [ ] 测试技能是否正常工作

---

**最后更新**：2026-04-03  
**仓库状态**：✅ 已同步最新修复结构