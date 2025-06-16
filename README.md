# Self-Documenting vRealize Orchestrator Workflows

This repository provides a complete solution for automatically generating and enhancing documentation for your vRealize Orchestrator (vRO) workflows. It leverages custom icons for improved visual clarity and bundles all required components into a single vRO package for easy deployment.

**Project Repository:** [vro-documentation](https://github.com/RoinGrindwald/vro-documentation)  
**Direct Package Download:** [com.broadcom.pso.vro.documentation.package (v1.2)](https://github.com/RoinGrindwald/vro-documentation/releases/download/v1.2/com.broadcom.pso.vro.documentation.package)

---

## Key Features

- **Automated Documentation Generation:**  
  Generate detailed documentation for individual workflows or entire workflow categories, including diagrams, tables, and step-by-step breakdowns.
- **Comprehensive Output:**  
  Documentation includes workflow metadata, inputs, outputs, variables, usages, dependencies, and a visual SVG schema.
- **Seamless vRO Integration:**  
  All components are delivered as native vRO workflows and Node.js actions for direct import and execution.

---

## Prerequisites

To use this solution, your vRO environment must meet the following requirements:

- **vRealize Orchestrator Enterprise License:**  
  Required for advanced features such as custom Node.js action environments.
- **Node.js Runtime (v20 recommended):**  
  The included action environment is configured for Node.js 20.
- **Node.js Package Dependencies:**  
  The package uses `node-graphviz` (for rendering diagrams) and `xmldom` (for SVG manipulation). These are managed by the vRO action environment.
- **Git Integration (Recommended):**  
  For version control and collaborative development.

---

## Solution Components

All components are delivered in the `com.broadcom.pso.vro.documentation.package` file:

- **Workflows:**
  - **Generate Workflow Documentation:**  
    Generates documentation for a single workflow and stores it as a vRO Resource Element.
  - **Generate Workflow Category Documentation:**  
    Generates documentation for all workflows within a selected category, storing each as a Resource Element.
  - **Generate All Workflows Documentation:**  
    Generates documentation for all workflows storing each as a Resource Element. You can exclude the inbuilt Library.

---

## How It Works

1. **Select a Workflow or Category:**  
   Run either the `Generate Workflow Documentation` (for a single workflow) or `Generate Workflow Category Documentation` (for all workflows in a category) or `Generate All Workflow Documentation` (for all workflows [Option to exclude `Library`]).
2. **Extract Metadata:**  
   The workflow extracts structure and metadata, converting it into a Graphviz DOT string.
3. **Render SVG Diagram:**  
   The DOT string is rendered into an SVG diagram using Node.js actions.
4. **Apply Icons:**  
   The SVG is post-processed to replace default node shapes with custom icons from the Resource Element.
5. **Store Documentation:**  
   The final documentation (Markdown/HTML and SVG) is saved as vRO Resource Elements for easy access and export.

---

## Usage

1. **Import the vRO Package:**  
   Download and import the package into your vRO environment.
2. **Run Documentation Workflows:**  
   - **Generate Workflow Documentation:**  
     Inputs: `workflow`, `type` (Markdown/HTML), `useClarity` (for Clarity CSS), `horizontal` (diagram orientation)
   - **Generate Workflow Category Documentation:**  
     Inputs: `workflowCategory`, `type` (Markdown/HTML), `useClarity`(for Clarity CSS), `horizontal` (diagram orientation)
   - Outputs are stored as Resource Elements.
3. **Export or Use Documentation:**  
   Retrieve the generated Resource Elements or export the Markdown/HTML/SVG files for use in wikis, documentation portals, or as PDFs.

See the [`documentation/`](documentation/) folder for real examples of the generated outputs.

---

## Workflow Inputs and Outputs

| Workflow                         | Inputs                                         | Outputs                          |
|-----------------------------------|------------------------------------------------|-----------------------------------|
| Generate Workflow Documentation   | `workflow`, `type`, `useClarity`, `horizontal` | `workflowDocumentation`           |
| Generate Workflow Category Documentation | `workflowCategory`, `type`, `useClarity`, `horizontal` | `result` (array of ResourceElements) |
| Generate All Workflow Documentation | `excludeLibrary` `type`, `useClarity`, horizontal` | `result` (array of ResourceElements)

---

## What Gets Generated

- Markdown and HTML documentation files for each workflow
- SVG diagrams
- All documentation is stored as vRO Resource Elements

---

## Acknowledgements

Thanks to the following open-source projects:

- **Graphviz:** Diagram rendering
- **node-graphviz:** Node.js Graphviz integration
- **xmldom:** SVG/XML parsing and manipulation

---

*For more details and examples, see the [`documentation/`](documentation/) folder.*