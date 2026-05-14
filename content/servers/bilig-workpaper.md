---
title: Bilig WorkPaper
description: Run formula-backed WorkPaper spreadsheets inside local MCP clients and coding-agent workflows with @bilig/headless.
category: Data Management
features:
- Data Summarization and Analysis
layout: server
created_at: 2026-05-14
updated_at: 2026-05-14
github_url: https://github.com/proompteng/bilig
website_url: https://proompteng.github.io/bilig/
license: MIT
free: true
---

## Overview

Bilig WorkPaper is a local stdio MCP server for spreadsheet-backed agent workflows. It exposes `@bilig/headless` so an MCP client can inspect workbook state, change input cells, read recalculated formula values, and persist the workbook as JSON without sending the spreadsheet to a hosted service.

The server is aimed at coding agents, Node services, and automation scripts that need spreadsheet logic but do not need a browser grid. The public package ships the `bilig-workpaper-mcp` binary on npm.

## Use Cases

- **Formula-backed agent tools:** Let an MCP client read a WorkPaper summary, change an input cell, and read the recalculated dependent value.
- **Workbook automation in Node:** Keep business rules in rows and formulas while a service route, queue worker, or CLI owns the workflow around them.
- **Reviewable spreadsheet state:** Persist a workbook as JSON, restore it, and verify that formulas still calculate to the expected values.

## Example

Install and run the server directly from npm:

    npm exec --package @bilig/headless -- bilig-workpaper-mcp

For Claude Desktop or another stdio MCP client, use an entry like this:

    {
      "mcpServers": {
        "bilig-workpaper": {
          "command": "npm",
          "args": ["exec", "--package", "@bilig/headless", "--", "bilig-workpaper-mcp"]
        }
      }
    }

The server exposes workbook tools such as `read_workpaper_summary` and `set_workpaper_input_cell`, which are documented in the repository and public site.