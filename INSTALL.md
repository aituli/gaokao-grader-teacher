# 安装指南

## 系统要求

- Python 3.8+（可选，用于高级功能）
- Claude Code 或 OpenClaw 环境

## 安装方式

### 方式一：Claude Code 安装

1. 打开 Claude Code 应用
2. 进入 Skill 管理界面
3. 选择"添加 Skill"
4. 输入 Skill 名称：`gaokao-grader-teacher`
5. 复制本 Skill 目录到 Claude Code 的 Skill 目录：
   ```bash
   # macOS/Linux
   cp -r /path/to/gaokao-grader-teacher ~/.claude/skills/
   
   # Windows
   xcopy /E /I C:\path\to\gaokao-grader-teacher %USERPROFILE%\.claude\skills\
   ```
6. 重启 Claude Code 或刷新 Skill 列表
7. 开始使用

### 方式二：OpenClaw 安装

1. 确保已安装 OpenClaw
2. 克隆或复制本 Skill 到 OpenClaw 工作目录：
   ```bash
   # 方法1：直接克隆（如果是Git仓库）
   git clone https://github.com/your-repo/gaokao-grader-teacher.git ~/.openclaw/workspace/skills/gaokao-grader-teacher
   
   # 方法2：手动复制
   mkdir -p ~/.openclaw/workspace/skills/gaokao-grader-teacher
   cp -r /path/to/gaokao-grader-teacher/* ~/.openclaw/workspace/skills/gaokao-grader-teacher/
   ```
3. 目录结构验证：
   ```
   ~/.openclaw/workspace/skills/gaokao-grader-teacher/
   ├── SKILL.md              # 主 Skill 文件
   ├── README.md             # 使用说明
   ├── README_ZH.md          # 中文项目介绍
   ├── INSTALL.md            # 本安装指南
   ├── meta.json             # 元数据
   ├── examples/             # 使用示例
   │   ├── math_example.md
   │   ├── chinese_example.md
   │   ├── english_example.md
   │   └── physics_example.md
   ├── docs/                 # 详细文档
   │   ├── scoring_criteria.md
   │   └── faq.md
   └── prompts/              # 提示模板
       └── grading_prompts.md
   ```
4. 重启 OpenClaw
5. 验证安装：
   ```bash
   openclaw skill list
   # 应能看到 gaokao-grader-teacher
   ```

### 方式三：项目本地安装

如果你有自己的 Claude Code 项目：

```bash
# 在项目根目录执行
mkdir -p .claude/skills
cp -r /path/to/gaokao-grader-teacher .claude/skills/
```

## 使用触发

安装完成后，通过以下方式触发 Skill：

### 自然语言触发
```
"帮我批改这道数学题"
"给这篇作文打个分"
"看看这道物理题的答案能得多少分"
```

### 命令触发
```
/gaokao-grader-teacher
```

## 输入格式

为了获得最佳评分效果，建议按以下格式提供信息：

```
【科目】数学/语文/英语/物理/化学/生物/政治/历史/地理
【题型】选择题/填空题/解答题/作文/...
【分值】（可选）该题满分
【题目】完整的题目内容
【学生答案】学生的作答内容
【标准答案】（可选）参考答案
```

## 验证安装

安装完成后，可以测试以下用例：

```
用户：请批改这道数学题
题目：求函数 f(x) = x² - 4x + 3 的极值
答案：f'(x) = 2x - 4 = 0，得 x = 2，极小值 f(2) = -1

期望输出：应给出分数（如 11/12 分）和详细的评分理由
```

## 卸载

如需卸载，删除 Skill 目录即可：

```bash
# Claude Code
rm -rf ~/.claude/skills/gaokao-grader-teacher

# OpenClaw
rm -rf ~/.openclaw/workspace/skills/gaokao-grader-teacher

# 项目本地
rm -rf .claude/skills/gaokao-grader-teacher
```

## 故障排除

### Skill 未加载
1. 检查目录结构是否正确
2. 确认 SKILL.md 文件存在且格式正确
3. 重启 Claude Code / OpenClaw

### 评分不准确
1. 检查是否提供了完整的题目信息
2. 确认科目类型是否正确
3. 参考 docs/scoring_criteria.md 了解详细评分标准

### 其他问题
查阅 docs/faq.md 获取常见问题解答。
