---
{"dg-publish":true,"dg-home":null,"tags":["thoughts"],"permalink":"/notes/05-thoughts-resources/yaml-database/","dgPassFrontmatter":true,"updated":"2026-07-16T16:03:08.520+05:30"}
---

# YAML Database

**A Reference-Based Content Storage Architecture for Obsidian and Large-Scale Knowledge Systems**

**Version:** 1.0  
**Status:** Concept Specification  
**Author:** Shatadru Bose  

---

## Abstract

YAML Database is a reference-based content storage architecture designed for Obsidian and similar knowledge management systems. Instead of storing large text, code, datasets, prompts, or documents directly inside notes, content is stored in a centralized database while notes contain only references and metadata.

The architecture separates identity from storage location. Every content object possesses a globally unique identifier (id) which serves as its primary identity. Human-readable filenames act as secondary identifiers and are independent of vault structure.

This model enables storage of extremely large content while maintaining lightweight notes, rapid navigation, efficient indexing, and scalable organization.

---

## 1. Introduction

Traditional Obsidian notes store content directly inside Markdown files.

**Example:**

```yaml
---
title: My Script
type: Python
---

print("Hello World")
```

While this approach is simple, it becomes problematic when dealing with:

* Large codebases
* Long research documents
* AI-generated outputs
* Datasets
* Archives
* Templates
* Prompt libraries

As content grows, notes become increasingly difficult to manage. YAML Database addresses this limitation by introducing a separation between metadata and content.

---

## 2. Core Principle

The core principle is:

> Notes contain references. The database contains content.

* A note acts as an index.
* The database acts as the content repository.

---

## 3. Database Schema

Each content record consists of six fields.

| Field | Description |
| :--- | :--- |
| **id** | Primary unique identifier |
| **file_name** | Secondary unique identifier |
| **type** | Content type |
| **value** | Actual content |
| **checksum** | Integrity hash |
| **last_modified** | Last update timestamp |

---

## 4. Example Record

**Database Entry**

| Field | Data |
| :--- | :--- |
| **ID** | `550e8400-e29b-41d4-a716-446655440000` |
| **File Name** | `Test/File.py` |
| **Type** | `Python` |
| **Value** | `print("Hello World")` |
| **Checksum** | `4f8d35e...` |
| **Last Modified** | `2026-06-15T15:30:00Z` |

---

## 5. Field Definitions

### 5.1 ID
The ID is the true identity of a content object.

**Example:** `550e8400-e29b-41d4-a716-446655440000`

**Characteristics:**
* Globally unique
* Immutable
* Independent of filename
* Independent of vault structure
* Survives renames

The ID should never change after creation.

### 5.2 File Name
The filename acts as a secondary identifier.

**Example:** `Test/File.py`

**Important:** The filename is NOT a filesystem path. It does not imply a strict directory structure. Instead, it is merely metadata. 

**Requirements:**
* Must be unique
* May contain slashes
* May be renamed
* Does not determine identity

### 5.3 Type
The type describes how content should be interpreted. The field is intentionally extensible.

**Examples:** Python, JavaScript, TypeScript, Markdown, Text, JSON, HTML, CSS, Java, Kotlin, Rust, C, C++, C#, SQL, YAML, XML, LaTeX, Bash, PowerShell, Prompt, Research, Dataset.

### 5.4 Value
The value field stores the actual content. It is the largest field in the database.

**Examples:**
* **Code:** `print("Hello World")`
* **Markdown:** `# Research Note`
* **JSON:** `{"name": "Example"}`
* **Text:** `Lorem ipsum...`

### 5.5 Checksum
Checksum stores a cryptographic hash.

**Example:** `a6c3e5f7f0b1...`

**Common algorithms:** SHA-256, SHA-512, BLAKE3

**Purposes:** Integrity verification, duplicate detection, synchronization validation, and corruption detection.

### 5.6 Last Modified
Stores the timestamp of the most recent change.

**Example:** `2026-06-15T15:30:00Z`

**Uses:** Sorting, synchronization, change tracking, and version management.

---

## 6. Example Obsidian Note

A note may contain only the metadata:

```yaml
---
id: 550e8400-e29b-41d4-a716-446655440000
file_name: Test/File.py
type: Python
---
```

The actual code is not stored here. Only references are stored.

---

## 7. SQL Schema

Example SQLite schema:

```sql
CREATE TABLE yaml_database (
    id TEXT PRIMARY KEY,
    file_name TEXT UNIQUE NOT NULL,
    type TEXT NOT NULL,
    value TEXT NOT NULL,
    checksum TEXT NOT NULL,
    last_modified TEXT NOT NULL
);
```

---

## 8. Architecture

```text
┌─────────────┐
│ Obsidian    │
│ Note        │
└──────┬──────┘
       │
       │ ID
       ▼
┌──────────────────────────┐
│ YAML Database            │
├──────────────────────────┤
│ id                       │
│ file_name                │
│ type                     │
│ value                    │
│ checksum                 │
│ last_modified            │
└──────────────────────────┘
```

---

## 9. Read Workflow

1. Open note.
2. Read ID.
3. Query database.
4. Locate record.
5. Retrieve content.
6. Display content.

**Flow:** Open Note → Read ID → Database Query → Fetch Record → Display Content

---

## 10. Write Workflow

**Flow:** Edit Content → Update Value → Recalculate Checksum → Update Timestamp → Save Record

---

## 11. Rename Workflow

Renaming affects only metadata.

* **Before:** `Test/File.py`
* **After:** `Projects/File.py`

**Results:**
* ID remains `550e8400-e29b-41d4-a716-446655440000`
* Content remains unchanged.
* References remain valid.

---

## 12. Content Size

YAML Database removes practical YAML limitations. Content is stored externally, so theoretical capacity depends entirely on the database engine, storage medium, memory, and software implementation. The architecture imposes no meaningful content-size restrictions (supports 1 KB to 1 GB+ depending on implementation).

---

## 13. Advantages

* **Lightweight Notes:** Notes remain small.
* **Fast Navigation:** Metadata can be browsed without loading content.
* **Large Content Support:** Huge codebases become manageable.
* **Stable Identity:** IDs survive renames.
* **Integrity Verification:** Checksums detect corruption.
* **Reusability:** Multiple notes may reference the same record.
* **Scalability:** Supports growth from small notes to massive repositories.

---

## 14. Use Cases

* **Software Development:** Store Python, Java, JavaScript, TypeScript, Rust, and Go projects.
* **AI Prompt Libraries:** Store System Prompts, Agent Definitions, Workflows, and Templates.
* **Research Archives:** Store Papers, Summaries, Sources, and References.
* **Knowledge Bases:** Store Articles, Notes, Datasets, and Documentation.
* **Digital Gardens:** Store Maps of Content, Permanent Notes, and Reference Material.

---

## 15. Future Extensions

**Potential future fields:**
* tags
* version
* parent_id
* created_at
* mime_type
* author
* source

**Potential future features:**
* Version history
* Chunked storage
* Compression
* Encryption
* Replication
* Multi-user collaboration

---

## 16. Design Philosophy

YAML Database follows six principles:

1.  **Identity Before Location:** Objects are identified by IDs, not paths.
2.  **Metadata Before Content:** Notes describe content. Databases store content.
3.  **Immutable Identity:** IDs never change.
4.  **Flexible Naming:** Filenames may change without breaking references.
5.  **Integrity First:** Checksums verify data correctness.
6.  **Scalability:** Architecture must support growth without redesign.

---

## 17. Formal Definition

A YAML Database object is defined as:

```text
Object =
{
    id,             → unique identity
    file_name,      → human-readable label
    type,           → content classification
    value,          → actual content
    checksum,       → integrity hash
    last_modified   → modification timestamp
}
```

---

## 18. Conclusion

YAML Database is a lightweight yet powerful architecture that separates metadata from content storage.

* The note becomes an index.
* The database becomes the repository.
* Identity is provided by globally unique IDs.
* Filenames become flexible labels rather than filesystem constraints.
* Checksums ensure integrity.
* Timestamps provide change tracking.

This separation creates a robust foundation for large-scale personal knowledge management, software repositories, AI workflows, digital gardens, research archives, and future extensible content systems.