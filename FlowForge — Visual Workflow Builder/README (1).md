# ⚡ FlowForge — Visual Workflow Automation Builder

A drag-and-drop visual workflow builder inspired by n8n and Make.com. Build, connect, and execute automation workflows entirely in the browser.

## 🚀 Features

- **14 Node Types** — Triggers (Webhook, Schedule, Email, Form) + Actions (Email, HTTP, Database, Slack, Google Sheets, OpenAI) + Logic (Condition, Delay, Loop, Transform)
- **Drag-and-Drop Canvas** — Drag nodes from the palette, reposition freely on the infinite canvas
- **Visual Connections** — Click "Connect" mode to draw edges between nodes with animated flow paths
- **Properties Panel** — Click any node to see and edit its configuration
- **Workflow Execution** — Animated step-by-step execution with live log output
- **Undo / Redo** — Full undo history for all changes
- **Save & Export** — Download workflow as JSON for backend import
- **Demo Loader** — One-click demo workflow: Webhook → Condition → OpenAI/Email → Slack/Database

## 🛠 Tech Stack

- Pure HTML/CSS/JavaScript — zero dependencies
- SVG for connection paths with CSS animations
- Drag-and-drop via HTML5 Drag API + mousemove events
- JSON workflow serialization

## 📂 File Structure

```
03-workflow-builder/
├── index.html    # Complete application
└── README.md     # This file
```

## 🏃 Quick Start

```bash
open index.html
```

## 💡 How to Use

1. **Drag** any node from the left palette onto the canvas
2. Switch to **Connect** mode (top toolbar)
3. Click a node's **right port** (output), then another node's **left port** (input)
4. Click any node to edit its **properties** in the right panel
5. Click **▶ Run Workflow** to execute with animation
6. Click **💾 Save** to export workflow as JSON

## 🔌 Production Integration

The exported `workflow.json` can be consumed by a backend executor:

```javascript
// Node.js workflow executor
const { nodes, connections } = JSON.parse(fs.readFileSync('workflow.json'));
const graph = buildDAG(nodes, connections);

for (const node of topologicalSort(graph)) {
  const result = await executeNode(node);
  passDataToChildren(node, result, graph);
}

async function executeNode(node) {
  switch(node.type) {
    case 'http': return fetch(node.config.URL);
    case 'openai': return callOpenAI(node.config.Prompt);
    case 'send_email': return sendgrid.send(node.config);
    case 'slack': return slackClient.chat.postMessage(node.config);
    // etc.
  }
}
```

## 🏗️ Architecture

```
Canvas (HTML + SVG)
    ↓ drag/drop/click events
State Manager (nodes[], connections[])
    ↓ serialize
Workflow JSON
    ↓ import
Backend Executor (Node.js / Python)
    ↓ execute
External APIs (Slack, Email, DB, OpenAI)
```

## 📝 License

MIT
