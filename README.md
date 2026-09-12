# 🧠 Developerscope Workflow Builder

A custom **React-based visual workflow builder** inspired by [n8n](https://n8n.io), allowing users to create, connect, and execute custom logic flows via a drag-and-drop node system.

<img src="https://github.com/berto6544-collab/2kai-workflow/blob/main/src/assets/Ui.png" width="100%"/>

## ✨ Features

- ⚙️ **Custom Node System** – Easily extendable node architecture via `nodeTypes`
- 🔗 **Connection-Based Flow** – Drag and connect nodes to define execution order
- 🎛 **Side Panel Configuration** – Select a node to update its config in a dynamic form panel
- 🧩 **Modular Components** – Fully component-based structure using `NodeComponent`, `RenderFormField`, and utility handlers
- 💡 **Execution Engine** – Runs nodes sequentially based on topological ordering
- 🔄 **Interactive Canvas** – Drag, pan, zoom, and reset view for a smooth UX
- 🗑️ **Safe Deletion** – Confirm before removing nodes (supports `Delete` key)
- 🧰 **Custom Node Execution Logic** – Defined via `NodeFunction`

## 🧱 Architecture Overview

```
src/
├── components/
│   ├── nodes.js           # Renders individual node components (icon, color, config)
│   └── PanelField.js      # Generates dynamic config forms for selected nodes
├── util/
│   ├── util.js            # Contains the logic to execute nodes in flow order
│   └── nodeArrays.js      # Defines node types, schema, icons, and categories
├── N8NWorkflowPlatform.js # Main app UI: canvas, panel, and node management
└── App.js                 # App entry point that renders the workflow platform
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/berto6544-collab/2kai-workflow.git
   cd 2kai-workflow
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm run dev
   ```

4. **Open your browser**
   
   Visit `http://localhost:5173` to view the application.

## 🧩 How to Add a Custom Node

### Step 1: Define Node Type

Update `nodeArrays.js` to define a new `nodeTypes` entry:

```javascript
{
  id: 'uniqueId',        // Unique identifier
  name: 'Display Name',   // Human-readable name
  icon: IconComponent,    // React icon component
  color: 'tailwind-classes', // Tailwind CSS classes for styling
  category: 'Category',    // Grouping category
  output: ['response','error'], // output response and error handling 
  input:['data'],          // input data 
}
```

### Step 2: Define Node Configuration

Update `nodeArrays.js` to define a new `nodeConfiguration`:

```javascript
configs = {
  myCustomNode: [
    {
  name: 'fieldName',      // Field identifier
  label: 'Field Label',   // Display label
  type: 'text|textarea|select|number', // Input type
  value: '',              // Default value
  placeholder: 'text',    // Placeholder text
  required: true|false,   // Validation requirement
  options: []             // For select type fields
}
  ]
}
```

### Step 3: Implement Node Logic

Add your custom execution logic in the appropriate utility files to handle your new node type.

## 🎯 Usage

1. **Add Nodes**: Drag nodes from the sidebar onto the canvas
2. **Connect Nodes**: Click and drag between node connection points to create flows
3. **Configure Nodes**: Select a node to edit its properties in the side panel
4. **Execute Workflow**: Run your complete workflow to see results
5. **Manage Canvas**: Use pan, zoom, and reset controls for better navigation

## 🔧 Configuration

### Node Types

Node types are defined in `src/util/nodeArrays.js` with the following structure:

```javascript
{
  id: 'uniqueId',        // Unique identifier
  name: 'Display Name',   // Human-readable name
  icon: IconComponent,    // React icon component
  color: 'tailwind-classes', // Tailwind CSS classes for styling
  category: 'Category'    // Grouping category
  output: ['response','error'] // output response and error handling 
  input:['data']          // input data 
}
```

### Node Configuration Schema

```javascript
{
  name: 'fieldName',      // Field identifier
  label: 'Field Label',   // Display label
  type: 'text|textarea|select|number', // Input type
  value: '',              // Default value
  placeholder: 'text',    // Placeholder text
  required: true|false,   // Validation requirement
  options: []             // For select type fields
}
```

## 🛠️ Development

### Project Structure

- **Components**: Reusable React components for nodes and forms
- **Utilities**: Core logic for node execution and configuration
- **Main Platform**: Primary application interface and state management

### Key Files

- `main.jsx`: Main application component
- `nodes.js`: Individual node rendering logic
- `PanelField.js`: Dynamic form field generation
- `util.js`: Workflow execution engine
- `nodeArrays.js`: Node definitions and configurations

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

MIT License © Roberto D'Amico

## 🐛 Issues

If you encounter any issues or have suggestions, please [open an issue](https://github.com/berto6544-collab/2kai-workflow/issues) on GitHub.

## 🙏 Acknowledgments

- Inspired by [n8n](https://n8n.io) workflow automation platform
- Built with React and modern web technologies
- Thanks to all contributors and users
