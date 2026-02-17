FlowForge — Visual Workflow Automation Builder

> Drag-and-drop workflow builder with 14 node types, visual connections, and animated execution.

![License](https://img.shields.io/badge/license-MIT-blue) ![Vanilla JS](https://img.shields.io/badge/vanilla-JS-yellow)

## 🚀 Quick Start
```bash
git clone https://github.com/YOUR_USERNAME/flowforge
open index.html
```

## ✨ Features
- **14 Node Types** — Triggers (Webhook, Schedule, Email, Form) + Actions (HTTP, Slack, OpenAI, Google Sheets) + Logic (IF, Loop, Delay, Transform)
- **Drag-and-Drop Canvas** — Drag from palette, reposition freely
- **Visual Connections** — Click Connect mode → draw edges with animated flow paths
- **Workflow Execution** — Step-by-step animated run with live log
- **Undo History** — Full undo for all canvas changes
- **JSON Export** — Download workflow for backend execution

## 💡 How to Use
1. Drag nodes from the left palette onto the canvas
2. Switch to **Connect** mode in the toolbar
3. Click a node's right port then another node's left port to connect
4. Click **▶ Run Workflow** to execute with animation
5. Click **Load Demo** to see a pre-built example

## 🔌 Backend Executor
```javascript
const { nodes, connections } = JSON.parse(fs.readFileSync('workflow.json'));

for (const node of topologicalSort(nodes, connections)) {
  const result = await executeNode(node);
  passDataToChildren(node, result);
}
```

## 📝 License
MIT
EOF

git init
git add .
git commit -m "Initial commit — FlowForge Visual Workflow Builder"
gh repo create flowforge --public --source=. --push
