# McDonald's Skills - 麦当劳优惠券自动领取工具

基于麦当劳官方MCP服务实现的Claude Code技能，支持查询优惠券、领取优惠券、查看活动日历等功能。

## 功能特性

- 优惠券查询：获取当前可用的麦当劳优惠券列表
- 优惠券领取：一键领取指定优惠券
- 活动日历：查看麦当劳最新的促销活动
- 会员权益：查询会员账户信息和权益

## 安装步骤

### 1. 获取MCP Token

访问 [麦当劳MCP平台](https://open.mcd.cn/mcp/doc) 注册并获取您的MCP Token。

### 2. 配置环境

复制配置文件并添加您的Token：

```bash
cp config.example.json ~/.claude/config.json
```

编辑 `~/.claude/config.json`，将 `your_token_here` 替换为您的实际Token。

### 3. 安装技能

将此技能目录复制到Claude的技能目录：

```bash
cp -r .claude/skills/mcdonalds-skills ~/.claude/skills/
```

## 使用方法

### 在Claude Code中使用

```
你: 查询一下麦当劳有哪些可用的优惠券
Claude: [调用query_coupons工具]

你: 帮我领取那个50% off的汉堡优惠券
Claude: [调用claim_coupon工具]
```

## 配置文件说明

配置文件 `~/.claude/config.json` 结构：

```json
{
  "mcpServers": {
    "mcdonalds": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-mcdonalds"],
      "env": {
        "MCD_TOKEN": "your_actual_token"
      }
    }
  }
}
```

## 相关链接

- 麦当劳MCP官方文档: https://open.mcd.cn/mcp/doc
- LobeHub MCP注册页: https://lobehub.com/zh/mcp/m-china-mcd-mcp-server
- GitHub项目: https://github.com/wyq09/mcdonalds-skills

## 注意事项

1. 本服务仅适用于中国大陆地区（不含港澳台）
2. 需要有效的麦当劳账户和MCP Token
3. 优惠券数量有限，先到先得

## 许可证

MIT License
