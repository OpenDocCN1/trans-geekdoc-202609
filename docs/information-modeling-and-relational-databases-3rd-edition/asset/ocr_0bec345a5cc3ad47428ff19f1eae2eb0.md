# Table 2.2 Zachman framework for enterprise architecture.

| | Data (what) | Function (how) | Network (where) | People (who) | Time (when) | Motivation (why) |
|---|---|---|---|---|---|---|
| Scope | | | | | | |
| Enterprise model | | | | | | |
| System model | | | | | | |
| Technology model | | | | | | |
| Detailed representations | | | | | | |

systems engineering project needs to consider which of these cells is relevant as well as how to map between the levels.

Row 1 (the scope) provides a very high-level view. Row 2 (the enterprise model) corresponds roughly to the conceptual or “owner view”. Row 3 (the system model) is basically the logical level, or “designer view”. Row 4 (the technology model) corresponds to most of the physical level, or “builder view”, with row 5 providing more detail in the “subcontractor” view. Enterprise level aspects appear in various cells.

This book focuses on column 1 (data) of rows 2 and 3, with some discussion of column 2 (function) and row 3. In practice, projects may involve other cells in this framework. For example, we may need to consider where the system will be deployed, who the stakeholders are, when system components are due, and why some business rules need to be enforced (columns 3–6).

Table 2.3 shows an extended four-schema framework based on both the four-schema approach and the Zachman framework. The logical and physical levels are refined into two layers. The persistent layer deals with data that persists between sessions: here we specify the structures to store data in a database (e.g., a relational schema). The transient layer deals with structures to temporarily store data in main memory during a session: the object model may be declared at the logic level as a class diagram and at the physical level as code structures in a programming language such as C# or Java.

# Table 2.3 Extended four-schema framework for system development.

| | Data (what) | Function (how) | Network (where) | People (who) | Time (when) | Motivation (why) |
|---|---|---|---|---|---|---|
| Conceptual | | | | | | |
| External | | | | | | |
| Logical-Persistent | | | | | | |
| Logical-Transient | | | | | | |
| Physical-Persistent | | | | | | |
| Physical-Transient | | | | | | |