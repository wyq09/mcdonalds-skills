---
name: mcdonalds-skills
description: 麦当劳优惠券自动领取工具,基于麦当劳 MCP 服务器实现。当用户请求查询麦当劳优惠券、领取优惠券、查看活动日历或管理麦当劳会员优惠时使用此 Skill。支持一键领取所有可用优惠券、查看已领取的优惠券列表、查询活动日历等功能。
---

# McDonald's Coupon Skill

## Overview
McDonald's China provides an official MCP (Model Context Protocol) service for querying and claiming coupons, viewing activity calendars, and managing membership benefits.

## Server Configuration

**MCP Server Address:**
```
https://mcp.mcd.cn/mcp-servers/mcd-mcp
```

**Required Configuration:**
- MCP Token (obtained from [McDonald's MCP Platform](https://open.mcd.cn/mcp/doc))

## When to Use

```
User request involves McDonald's China?
├── Query/claim coupons? → Use this skill
├── View activity calendar? → Use this skill
├── Membership benefits? → Use this skill
└── Other regions/operations → Do not use
```

**Use when:**
- User wants to query available McDonald's coupons
- User wants to claim McDonald's coupons
- User asks about McDonald's promotional activities/calendar
- User needs McDonald's membership information

**Do NOT use when:**
- User is outside mainland China (service only available in China)
- User wants to place food orders
- User needs store location/information

## Available Tools

| Tool | Description |
|------|-------------|
| `query_coupons` | Query available McDonald's coupons |
| `claim_coupon` | Claim a specific coupon |
| `activity_calendar` | Query promotional activity calendar |
| `member_benefits` | Query membership account benefits |

## Configuration File

Store your MCP token in `~/.claude/config.json`:

```json
{
  "mcpServers": {
    "mcdonalds": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-mcdonalds"],
      "env": {
        "MCD_TOKEN": "your_token_here"
      }
    }
  }
}
```

## Usage Examples

**Query available coupons:**
```
User: "What McDonald's coupons are available?"
→ Call query_coupons tool
```

**Claim a coupon:**
```
User: "Claim the 50% off burger coupon"
→ Call claim_coupon with coupon_id
```

**View activities:**
```
User: "Show me this week's McDonald's promotions"
→ Call activity_calendar tool
```

## Common Mistakes

| Mistake | Correct Approach |
|---------|------------------|
| Assuming global availability | Service only for mainland China |
| Forgetting to configure token | Token required for all operations |
| Confusing with ordering | This is coupons/promotions only, not food ordering |

## References

- Official Documentation: https://open.mcd.cn/mcp/doc
- LobeHub Registry: https://lobehub.com/zh/mcp/m-china-mcd-mcp-server
