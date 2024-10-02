# Generating MindMaps with LLMs like ChatGPT for KnowledgeBase Builder import

## Overview

This guide explains how to use large language models (LLMs) like ChatGPT to generate mind maps in JSON format that can be imported into the **KnowledgeBase Builder** app. The JSON structure must adhere to a specific format to be successfully imported via the app's menu: `KnowledgeBase -> Import / Export -> Import JSON Data`.

## Generating MindMaps with LLMs

LLMs can be used to create structured mind maps by generating JSON files that describe nodes, edges, and categories in the format required by **KnowledgeBase Builder**. The structure of this JSON follows a particular schema, which includes nodes (representing ideas or concepts), edges (connections between nodes), and categories (classifications for nodes and edges).

### JSON Structure

A basic JSON file for a mind map in **KnowledgeBase Builder** consists of the following key components:

1. **Nodes**: Represent the individual ideas or concepts in the mind map. Each node has:
    - An `id`: A unique identifier.
    - A `label`: A description of the node.
    - A `description`: Additional information about the node.
    - A `note`: Optional detailed notes related to the node.
    - A `categoryId`: The category that the node belongs to.

2. **Edges**: Represent connections or relationships between nodes. Each edge has:
    - An `id`: A unique identifier.
    - A `source`: The `id` of the starting node.
    - A `target`: The `id` of the connected node.
    - Optional properties like `label` (name of the connection) and `description` (additional information about the connection).

3. **NodeCategories**: The categories assigned to nodes for classification.

4. **EdgeCategories**: The categories assigned to edges for classification.

5. **Diagram Properties**: Additional settings related to the diagram.

### Example JSON Format

Below is a simplified example of how the JSON should be structured:

```json
{
  "nodes": [
    {
      "id": 1,
      "label": "<html><span style=\"display:inline-table\"><span style=\"display:table-cell;vertical-align:middle;font-size:3em;\">💡</span><span style=\"display:table-cell;vertical-align:middle\"> Idea 1</span></span></html>",
      "description": "Description 1",
      "categoryId": 1
    },
    {
      "id": 2,
      "label": "<html><span style=\"display:inline-table\"><span style=\"display:table-cell;vertical-align:middle;font-size:3em;\">🔍</span><span style=\"display:table-cell;vertical-align:middle\"> Idea 2</span></span></html>",
      "description": "Description 2",
      "categoryId": 2
    }
  ],
  "edges": [
    {
      "id": 1,
      "source": 1,
      "target": 2,
      "label": "Connection 1",
      "description": "This is a connection between Idea 1 and Idea 2.",
      "categoryId": 1
    }
  ],
  "nodeCategories": [
    {
      "id": 1,
      "name": "Category1"
    },
    {
      "id": 2,
      "name": "Category2"
    }
  ],
  "edgeCategories": [
    {
      "id": 1,
      "name": "line category"
    }
  ],
  "diagram": {
    "properties": {
      "tv": 0
    }
  }
}
```

### How to Generate JSON Using ChatGPT

You can prompt an LLM, such as ChatGPT, to generate JSON files like the example above by asking it to create a mind map with specific nodes, edges, and categories. For example, you can use the following prompt:

**Prompt Example:**
```
Create a JSON file for a mind map with the following nodes:
1. Idea 1 (💡) with a description of "Description 1"
2. Idea 2 (🔍) with a description of "Description 2"
Also, create a connection between these ideas named "Connection 1" with the description "This is a connection between Idea 1 and Idea 2."
```

The generated JSON can then be copied and saved as a `.json` file.

## Importing the JSON File into KnowledgeBase Builder

Once the JSON file has been generated and saved, you can import it into **KnowledgeBase Builder** by following these steps:

1. **Open KnowledgeBase Builder**.
2. Navigate to the menu: `KnowledgeBase -> Import / Export -> Import JSON Data`.
3. Select the JSON file you have created and click **Import**.

The mind map will now appear in the **KnowledgeBase Builder** interface with the nodes and connections defined in the JSON file.

## Conclusion

By leveraging LLMs like ChatGPT, you can quickly generate complex mind maps in JSON format that are compatible with **KnowledgeBase Builder**. This allows for faster and more efficient mind map creation, enhancing your knowledge management workflow.
