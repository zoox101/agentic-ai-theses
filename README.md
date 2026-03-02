| Thesis | Title |
|---|---|
| 1 | [[#1. The local file system is the best foundation for agent work]] |
| 2 | [[#2. A knowledge base is mandatory]] |
| 3 | [[#3. Knowledge base should be graph based]] |
| 4 | [[#4. Inter-linked Markdown files as the knowledge graph]] |
| 5 | [[#5. Code should be co-located with documentation]] |
| 6 | [[#6. AI code has a trust and control deficit]] |
| 7 | [[#7. Humans should interact with a schema, not code]] |
| 8 | [[#8. The schema should be textual, compilable, and lintable]] |
| 9 | [[#9. The schema should be a data flow DAG]] |
| 10 | [[#10. Functional programming aligns with data flow]] |
| 11 | [[#11. Code, tests, and documentation are equivalent]] |
| 12 | [[#12. A function is a folder]] |
| 13 | [[#13. Extreme standardization is required]] |
| 14 | [[#14. Tests are data points, not code]] |
| 15 | [[#15. Test execution should be generated]] |
| 16 | [[#16. The schema should map directly to the file structure]] |
| 17 | [[#17. The architecture should be fractal]] |
| 18 | [[#18. The schema should be visually editable]] |
| 19 | [[#19. Context switching is the bottleneck]] |
| 20 | [[#20. A single orchestrator agent should interface with humans]] |
| 21 | [[#21. Tasks are Markdown files]] |
| 22 | [[#22. Git worktrees enable parallel agents]] |
| 23 | [[#23. Structured knowledge eliminates skill files]] |

## 1. The local file system is the best foundation for agent work

Modern agent systems often default to:

- Databases  
- API connectors  
- Cloud-managed storage  
- Hidden runtime state  

These introduce:

- Infrastructure complexity  
- Deployment coupling  
- Hidden failure modes  
- Access control headaches  
- Serialization mismatches  

The file system avoids all of this.

It is:

- Universally available  
- Transparent  
- Human-readable  
- Backed up easily  
- Git-compatible  
- Inspectable without tooling  

Most importantly:

Agents are trained on text.  
Files are text.  

The file system is the lowest-friction shared abstraction between humans and agents.

It requires:

- No connectors  
- No runtime scaffolding  
- No schema migrations  
- No infrastructure orchestration  

It is deterministic state.

That makes it ideal.


## 2. A knowledge base is mandatory

Agents possess broad internet knowledge.  
They lack *your* knowledge.

They do not know:

- Your company structure  
- Your naming conventions  
- Your financial definitions  
- Your application constraints  
- Your preferences  

This knowledge should be externalized.

## 3. Knowledge base should be graph based

A tree is insufficient because knowledge is not hierarchical.  
It is relational.

Example:

- A "firetruck" is both red and a truck.  
- A "KPI" may belong to finance and operations.  
- A "customer" may connect to sales, support, and billing.  

Therefore:

> Knowledge should be stored as a graph, not a tree.

A graph allows:

- Cross-domain relationships  
- Bidirectional traversal  
- Emergent contextual linking  
- Recontextualization without embeddings  

This avoids probabilistic retrieval systems where context is guessed.

Instead, relationships are explicit.


## 4. Inter-linked Markdown files as the knowledge graph

The ideal implementation is:

- Markdown files  
- Stored locally  
- Interconnected via links  
- Visualized as a graph  

A Markdown-first graph workspace provides:

- Markdown-native storage  
- Link graph visualization  
- Backlinking  
- Search  
- Local-first design  

Advantages:

- Human-readable  
- Agent-readable  
- Git-compatible  
- No database required  
- No API layer required  

Unlike RAG:

- Relationships are deliberate.  
- Context is not approximate.  
- Relevance is not probabilistic.  
- Structure is inspectable.  

The vault becomes:

> The canonical knowledge layer of the system.


## 5. Code should be co-located with documentation

Traditional systems separate:

- Documentation  
- Code  
- Tests  
- Architecture diagrams  

This fragments understanding.

Instead:

```
function_name/
	function_name.py
	function_name.md
	examples/
		0000/
			input.json
			output.json
		...
	utils/
```

The rule:

> Articles describing a system and code implementing it should be co-located.

This creates:

- Context locality  
- Reduced cognitive overhead  
- Faster agent navigation  
- Faster human auditing  
- Stronger architectural cohesion  

The vault is not “documentation about code.”

It is the environment in which code lives.


## 6. AI code has a trust and control deficit

Human-written code carries implicit trust:

- Style familiarity  
- Architectural intuition  
- Known design philosophy  
- Review familiarity  

AI-generated code lacks that.

Problems include:

- Hallucinated assumptions  
- Missing context  
- Style drift  
- Hidden coupling  
- Poor test coverage  
- UI validation blind spots  

Trust requires:

- Observability  
- Determinism  
- Structural visibility  
- Behavioral guarantees  

Understandability is currently expensive because:

- Reading code scales linearly.  
- Generated code scales exponentially.  

We should reduce the cost of comprehension.


## 7. Humans should interact with a schema, not code

Code is implementation detail.

Humans should define:

- Components  
- Data flow  
- Transformation boundaries  
- Interfaces  
- Constraints  

This mirrors how architects operate.

The schema becomes:

> The contract the code should obey.

AI agents implement.  
Humans design.


## 8. The schema should be textual, compilable, and lintable

The schema should:

1. Compile to diagrams.  
2. Compile to type definitions.  
3. Be readable by agents.  
4. Be statically lintable.  
5. Avoid image-only representation.  

UML alone is insufficient because:

- It is visual.  
- Agents process text better than images.  
- It cannot be linted without external tooling.  

Therefore:

> We need a text-based schema language that compiles into multiple artifacts.

The schema becomes the canonical source.

Everything else derives from it.


## 9. The schema should be a data flow DAG

The most useful mental model of a system is:

Inputs → Transformations → Outputs

This is a Directed Acyclic Graph.

Why DAG?

- No circular reasoning  
- Clear topological order  
- Deterministic execution  
- Clear dependency boundaries  

Example:

    Stock API → Data Normalization → Metric Computation → Dashboard Renderer

Understanding becomes immediate.

Modification becomes surgical.


## 10. Functional programming aligns with data flow

Data flow diagrams describe:

- Nodes  
- Transformations  
- Pure mappings  

Functional programming mirrors this.

Benefits:

- Pure input → output mapping  
- Weak coupling  
- Deterministic behavior  
- Easy testability  
- Parallelizability  

Testing becomes trivial:

    f(input) = output

Object-oriented systems obscure data flow.

Functional systems reveal it.


## 11. Code, tests, and documentation are equivalent

A function can be defined by:

1. Code (equation)  
2. Tests (points on the curve)  
3. Documentation (verbal definition)  

These are mathematically equivalent.

Drift between them causes bugs.

Therefore:

> They should be kept together.


## 12. A function is a folder

Instead of:

    add.py

We define:

    /add
        implementation.py
        tests.json
        README.md

Advantages:

- Atomic movement  
- Synchronization ease  
- Full context portability  
- Structural clarity  

Copy the folder → copy the function.


## 13. Extreme standardization is required

Human code tolerates stylistic diversity.

AI-generated systems cannot.

When generation volume increases:

> Standardization becomes mandatory.

Every function should follow identical structure.

Humans should instantly locate:

- Implementation  
- Tests  
- Documentation  

Without hunting.


## 14. Tests are data points, not code

Mathematically:

Tests are points on a curve.

Instead of executable test code, we define:

    {
      "input": { "a": 1, "b": 2 },
      "output": 3
    }

Benefits:

- Easier inspection  
- Faster reasoning  
- No abstraction overhead  
- Easier modification  
- Machine-readable and human-readable  


## 15. Test execution should be generated

A global framework should:

- Parse JSON tests  
- Auto-generate pytest-compatible wrappers  
- Execute systematically  

Function folders contain test data.

Execution logic is centralized.


## 16. The schema should map directly to the file structure

You should be able to:

- Look at a schema node  
- Immediately find its folder  

Schema and file system should be isomorphic.


## 17. The architecture should be fractal

Each node:

- Has inputs  
- Has outputs  
- Has transformations  

At every scale:

- Application  
- Module  
- Function  
- Sub-function  

The structure repeats recursively.

Understanding scales smoothly.


## 18. The schema should be visually editable

Humans should:

- Drag nodes  
- Rewire connections  
- Collapse layers  
- Expand subgraphs  
- See updates in real time  

Agents update the schema.

Humans interact visually.


## 19. Context switching is the bottleneck

Managing multiple coding agents causes:

- Interrupt-driven workflow  
- Fragmented context  
- High cognitive tax  
- Inefficiency  

This is unsustainable.


## 20. A single orchestrator agent should interface with humans

Humans interact with:

> One fast coordinating agent.

That agent:

- Spawns sub-agents  
- Tracks state  
- Queues tasks  
- Aggregates results  
- Shields humans from latency  

Humans maintain one continuous thread.


## 21. Tasks are Markdown files

Each task is:

    /tasks/implement_dashboard.md

Metadata:

    status: in_progress
    assigned_to: agent_4
    priority: high

Advantages:

- Observable workflow  
- Parallel safety  
- Auditability  
- Stateless orchestration  
- Reduced conflict  


## 22. Git worktrees enable parallel agents

All file-based systems should use Git.

Agents:

- Operate in worktrees  
- Isolate changes  
- Submit branches  
- Merge via a merge agent  

Git provides:

- Version history  
- Rollback safety  
- Conflict management  
- Parallel development  
- Forensic traceability  


## 23. Structured knowledge eliminates skill files

Many systems define “skills” as:

- Tool definitions  
- External capability configs  
- Prompt scaffolding  

In a vault-based architecture:

- Code lives in the vault.  
- Documentation lives in the vault.  
- Tests live in the vault.  
- Schema lives in the vault.  

Agents discover capabilities by:

- Searching  
- Following links  
- Traversing schema  
- Inspecting function folders  

The only built-in skill required is:

> How to navigate and query the vault.

The vault is not documentation.

It is the system.
