# OpenFundraise for Claude, ChatGPT and Codex

OpenFundraise is a fundraising platform for nonprofits. This plugin connects Claude, Claude Code, ChatGPT and Codex to your OpenFundraise organization so you can ask about fundraising totals and trends, campaigns and goals, individual donations and supporters, events and ticket sales, recurring giving, donor traffic sources, checkout conversion, A/B experiments, peer-to-peer pages and payouts.

You sign in with your OpenFundraise account. The assistant sees only the organizations you belong to, limited to what your role can already see in the OpenFundraise dashboard. With your approval it can resend a donation receipt to the donor's email on file or add a staff note to a supporter. It cannot move money, refund gifts or message donors.

## What's in the plugin

- A remote MCP server at `https://openfundraise.org/mcp/dashboard`. It uses OAuth sign-in with your OpenFundraise account; no API keys are stored in the plugin.
- A skill that explains which tool answers which question and how OpenFundraise reports amounts.

## Install

**Claude Code**

```
claude plugin marketplace add OpenFundraise/openfundraise-plugin
claude plugin install openfundraise@openfundraise
```

Then run `/mcp` in Claude Code, choose **openfundraise** and sign in with your OpenFundraise account.

**Claude, ChatGPT and Codex**

Install OpenFundraise from the Claude directory or the ChatGPT plugin directory, then sign in when prompted.

## What the plugin sends and stores

The plugin talks only to `openfundraise.org`. Each tool call sends the tool's arguments to OpenFundraise, which checks your role and returns the requested data.

OpenFundraise records usage analytics for each call in PostHog: your OpenFundraise user ID, name and email, the organization, the tool name, how long it took, whether it failed, the assistant app, and the model and short reason the assistant reports. Emails and phone numbers are removed from that reason. Tool arguments and results, which contain donor data, are not sent to PostHog. Write actions are also recorded in your organization's audit log. See the [OpenFundraise privacy policy](https://openfundraise.org/privacy).

To disconnect, remove the connection in your assistant's settings.

## Support

Email support@openfundraise.org or visit [openfundraise.org/contact](https://openfundraise.org/contact). Documentation: [openfundraise.org/developers/mcp](https://openfundraise.org/developers/mcp).
