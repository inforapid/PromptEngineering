# Generating MindMaps with ChatGPT for KnowledgeBase Builder

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

You can guide LLMs to generate a mind map in JSON format by giving them a prompt that includes a sample JSON structure, illustrating how the data should be structured.

#### Example LLM Prompt:

```
Create a mind map in JSON format for the topic "YOUR_TOPIC" using the language "YOUR_LANGUAGE".
Each node should have a html formated label that begins with an emoji and a description.
The mind map should contain at least 25 nodes with about 3 sentences of description and edges with labels
as a hierarchic tree with at least 3 levels where every node is connected with a parent node.
Generate only the json data, no explanation. Use the following JSON structure as a reference:
{
  "nodes": [
    {
      "id": 1,
      "label": "<html><span style=\"display:inline-table\"><span style=\"display:table-cell;vertical-align:middle;font-size:3em;\">💡</span><span style=\"display:table-cell;vertical-align:middle\"> Name 1</span></span></html>",
      "description": "Description 1",
      "categoryId": 1
    },
    {
      "id": 2,
      "label": "<html><span style=\"display:inline-table\"><span style=\"display:table-cell;vertical-align:middle;font-size:3em;\">🔍</span><span style=\"display:table-cell;vertical-align:middle\"> Name 2</span></span></html>",
      "description": "Description 2",
      "categoryId": 2
    }
  ],
  "edges": [
    {
      "id": 1,
      "source": 1,
      "target": 2,
      "label": "Line 1",
      "description": "Line Description 1",
      "categoryId": 1
    }
  ],
  "nodeCategories": [
    {
      "id": 1,
      "name": "Category1"
    }
  ],
  "edgeCategories": [
    {
      "id": 1,
      "name": "Line category"
    }
  ]
}
```

Replace `"YOUR_TOPIC"` with the subject of your mind map, and `"YOUR_LANGUAGE"` with the language in which you'd like the mind map to be generated. The prompt instructs the LLM to output the structure in the correct JSON format.

The generated JSON can then be copied to the clipboard or saved as a `.json` file.

## Importing the JSON Mind Map into KnowledgeBase Builder

Once the JSON mind map has been generated and copied or saved, you can import it into **KnowledgeBase Builder** by following these steps:

1. **Open KnowledgeBase Builder**.
2. Navigate to the menu: `KnowledgeBase -> Import / Export -> Import JSON Data`.
3. Select the JSON file you have created or paste the JSON data into the import dialog and click **Import**.

The mind map will now appear in the **KnowledgeBase Builder** with the nodes and connections defined in the JSON file.

## Conclusion

By leveraging LLMs like ChatGPT, you can quickly generate complex mind maps in JSON format that are compatible with **KnowledgeBase Builder**. This allows for faster and more efficient mind map creation, enhancing your knowledge management workflow.
