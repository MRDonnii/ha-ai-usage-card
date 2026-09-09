# HA AI Usage Card

A responsive Home Assistant Lovelace card that combines usage limits from
multiple AI accounts in one dashboard surface.

Each account panel shows connection state, plan, remaining five-hour and weekly
capacity, reset times, latest update, optional extra usage or credits, and a
refresh action. The grid automatically scales for one, two, or several accounts.

## Installation

Add this repository to HACS as a custom **Dashboard** repository, or copy
`ha-ai-usage-card.js` into `config/www/ha-ai-usage-card/` and register:

```yaml
url: /local/ha-ai-usage-card/ha-ai-usage-card.js
type: module
```

## Example

```yaml
type: custom:ha-ai-usage-card
title: AI usage
accounts:
  - name: ChatGPT
    provider: OpenAI / Codex
    icon: mdi:message-processing-outline
    connected: binary_sensor.chatgpt_usage_connected
    limit_reached: binary_sensor.chatgpt_usage_limit_reached
    plan: sensor.chatgpt_usage_plan
    session_remaining: sensor.chatgpt_usage_5_hour_remaining
    session_reset: sensor.chatgpt_usage_5_hour_reset
    weekly_remaining: sensor.chatgpt_usage_weekly_remaining
    weekly_reset: sensor.chatgpt_usage_weekly_reset
    last_update: sensor.chatgpt_usage_last_successful_update
    credits: sensor.chatgpt_usage_reset_credits_available
    refresh: button.chatgpt_usage_refresh_usage
```

Only the `accounts` list is required. Missing optional sensors are displayed as
unavailable without breaking the card.
