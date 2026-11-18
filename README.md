# ShellGuard - Shell 命令安全审计工具

## 项目名称
**ShellGuard**

## GitHub Repository Description
Real-time shell command safety audit with intelligent risk analysis. Prevent command injection, detect dangerous operations, and enforce shell security policies. Zero dependencies, pure Python.

## 项目描述
ShellGuard 是一个实时 Shell 命令安全审计工具，专门解决开发环境中 shell 命令注入风险和安全操作问题。

### 核心痛点

1. **命令注入风险**：不安全的命令构造导致注入攻击
2. **危险操作无预警**：rm -rf / 等危险命令缺乏确认机制
3. **权限滥用**：敏感命令执行缺乏审计
4. **历史命令污染**：恶意注入的命令入侵历史
5. **CI/CD 安全**：自动化流水线中的命令安全

## 核心功能

### 1. 实时命令审计 🔍
- 命令执行前实时分析
- 危险命令检测
- 风险等级评分

### 2. 危险操作防护 ⚠️
- rm -rf / 等命令拦截
- 写操作到系统目录检测
- 权限提升操作预警

### 3. 注入攻击检测 🛡️
- 命令注入模式识别
- 子进程注入检测
- 环境变量篡改检测

### 4. 审计日志 📋
- 所有命令执行记录
- 风险操作报告
- 合规审计支持

## 技术特性

- ✅ 纯 Python，零第三方依赖
- ✅ 实时审计，不影响执行性能
- ✅ 可扩展规则引擎
- ✅ 确定性输出
- ✅ 轻量级设计

## 使用示例

```python
from shellguard import ShellGuard, RiskLevel

guard = ShellGuard()

# 检查命令安全性
risk = guard.analyze("rm -rf /tmp/test")
print(f"风险等级: {risk.level}")
print(f"原因: {risk.reason}")
print(f"建议: {risk.suggestion}")

# 实时审计
guard.audit_command("cat /etc/passwd")  # 高风险

# 生成安全报告
report = guard.generate_report()
print(report)
```

## 规则配置

```json
{
  "rules": [
    {
      "pattern": "rm -rf/",
      "risk_level": "CRITICAL",
      "action": "block"
    },
    {
      "pattern": "sudo [a-z]+",
      "risk_level": "HIGH",
      "action": "warn"
    }
  ]
}
```

## 安装

```bash
git clone https://github.com/shellguard/shellguard.git
cd shellguard
pip install -e .
```

## License
MIT License