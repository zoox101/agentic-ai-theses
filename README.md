| Thesis | Title |
|---|---|
| 1 | [[#1. The local file system is the best foundation for agent work]] |
| 2 | [[#2. A knowledge base is mandatory]] |
| 3 | [[#3. A knowledge base should be graph based]] |
| 4 | [[#4. Inter-linked Markdown files are the best implementation for the knowledge graph]] |
| 5 | [[#5. Code should be co-located with documentation in the same domain folders]] |
| 6 | [[#6. AI-generated code has a trust and control deficit]] |
| 7 | [[#7. Humans should interact with a schema instead of raw implementation code]] |
| 8 | [[#8. The schema should be textual, compilable, and lintable]] |
| 9 | [[#9. The schema should be represented as a data-flow DAG]] |
| 10 | [[#10. Functional programming aligns best with this data-flow architecture]] |
| 11 | [[#11. Functions can be defined equivalently by code, tests, and documentation]] |
| 12 | [[#12. A function should be treated as a folder, not just a file]] |
| 13 | [[#13. Function folders should follow extreme standardization]] |
| 14 | [[#14. Tests should be represented as data points rather than handwritten test code]] |
| 15 | [[#15. Test execution code should be generated from standardized test data]] |
| 16 | [[#16. The schema should map directly to the file system]] |
| 17 | [[#17. The schema and file system should be recursive and fractal]] |
| 18 | [[#18. Humans should have a live graphical editor for the schema]] |
| 19 | [[#19. Human context switching across many agents is a primary bottleneck]] |
| 20 | [[#20. Humans should interface with one fast orchestrator agent]] |
| 21 | [[#21. Multi-agent execution should be file-based and Git-native]] |

## 1. The local file system is the best foundation for agent work
For developer-facing agent systems, the local file system is the most practical default substrate. It is universally available, transparent, and directly compatible with how coding agents and humans both inspect and edit state. Compared with database-first designs, it removes connector overhead and reduces operational complexity while preserving hackability.

## 2. A knowledge base is mandatory
General model knowledge is not enough for production work in a real codebase. Agents need explicit access to your domain language, constraints, naming conventions, and business context to make correct implementation decisions. A maintained knowledge base is therefore a core dependency, not optional documentation.

## 3. A knowledge base should be graph based
Developer knowledge is relational, not strictly hierarchical. Concepts routinely cross boundaries between product, finance, operations, architecture, and implementation, so tree-only structures lose important links. A graph model captures these cross-domain relationships directly and improves retrieval precision.

## 4. Inter-linked Markdown files are the best implementation for the knowledge graph
Inter-linked Markdown on local disk gives you a graph that is readable by both humans and agents without extra infrastructure. Developers can review and diff it in Git, and agents can traverse it as plain text using predictable link structure. This keeps knowledge explicit, inspectable, and easy to evolve.

## 5. Code should be co-located with documentation in the same domain folders
When code and docs are split across systems, comprehension cost rises and drift accelerates. Co-location keeps implementation, domain notes, and supporting artifacts in one place, which shortens navigation loops for developers and agents. This is especially effective for domain-heavy areas like finance, billing, or analytics.

## 6. AI-generated code has a trust and control deficit
The core challenge with AI-generated code is governance, not throughput. Developers need confidence that behavior matches requirements, style expectations, and architectural constraints, but that confidence is expensive when outputs are opaque. Trust improves only when control, observability, and reviewability are designed into the workflow.

## 7. Humans should interact with a schema instead of raw implementation code
Humans should define structure, boundaries, and requirements at the architecture layer, then let agents implement within that contract. This mirrors effective engineering practice where design intent is specified before coding begins. A schema-first workflow also makes review discussions about system behavior instead of file-by-file trivia.

## 8. The schema should be textual, compilable, and lintable
A useful schema must be executable as engineering input, not just a static picture. It should compile to visual diagrams for human comprehension and to typed artifacts for implementation constraints, and it should be lintable for fast static validation. Text-first representation ensures agents can consume the schema reliably.

## 9. The schema should be represented as a data-flow DAG
A data-flow DAG is a strong default mental model for most application logic: inputs, transformations, outputs. It gives developers a clear topological ordering and helps isolate changes to specific edges and nodes. For pipelines and service composition, this model makes system behavior easier to reason about under change.

## 10. Functional programming aligns best with this data-flow architecture
Data-flow architectures map naturally onto functional composition. Pure or mostly pure functions provide explicit input-output behavior, which improves testability and reduces hidden coupling. For agent-generated code, this explicitness is a major advantage during review, debugging, and regeneration.

## 11. Functions can be defined equivalently by code, tests, and documentation
For practical engineering, function behavior is described by three equivalent surfaces: implementation, examples/tests, and prose contract. If any one surface drifts, bugs and misunderstandings appear. Treating all three as first-class definitions creates stronger alignment between author intent and runtime behavior.

## 12. A function should be treated as a folder, not just a file
A function should be packaged as an atomic unit that includes code, tests, docs, and supporting assets. This structure makes copying, refactoring, and ownership transfer safer because behavior context moves with implementation. It also gives developers a predictable place to find the full definition of what a function does.

## 13. Function folders should follow extreme standardization
In high-volume AI-assisted code generation, consistency matters more than local stylistic optimization. Standardized folder layout reduces search time, lowers onboarding cost, and improves review throughput across teams. Developers should be able to jump from a schema node to a known file pattern immediately.

## 14. Tests should be represented as data points rather than handwritten test code
Many tests are fundamentally input-output assertions and are better stored as explicit data points. Representing these cases as structured data (for example JSON input/output pairs) makes behavior review faster and less abstract for developers. It also keeps test intent independent from test-runner boilerplate.

## 15. Test execution code should be generated from standardized test data
If tests are stored as data, execution scaffolding should be generated centrally. A shared runner can translate standardized cases into framework-specific tests, eliminating repetitive per-function harness code. This keeps function folders focused on behavior while preserving compatibility with existing tooling like Pytest.

## 16. The schema should map directly to the file system
Schema structure and repository structure should correspond directly. Developers should be able to infer where code lives from architecture definitions without extra lookup layers. This one-to-one mapping improves discoverability, onboarding, and automation.

## 17. The schema and file system should be recursive and fractal
The same input-transform-output shape should recur from top-level system architecture down to nested implementation units. This recursive pattern lets developers zoom between abstraction levels without switching mental models. A fractal structure keeps large systems understandable as they scale.

## 18. Humans should have a live graphical editor for the schema
Schema editing should not require prompt gymnastics for every structural change. Developers need direct visual operations such as drag, rewire, collapse, and expand, with real-time updates from agent edits. A live editor increases design velocity and reduces translation friction between intent and implementation.

## 19. Human context switching across many agents is a primary bottleneck
Managing many concurrent coding agents creates heavy cognitive overhead for developers. Asynchronous returns from multiple threads force constant context reloading, which degrades quality and speed. The limiting factor quickly becomes human coordination bandwidth, not model capability.

## 20. Humans should interface with one fast orchestrator agent
A single fast orchestrator agent should be the primary interface for developers. It should maintain conversation continuity, dispatch specialized sub-agents, and summarize results without forcing the user to juggle multiple threads. This preserves focus while still enabling parallel execution behind the scenes.

## 21. Multi-agent execution should be file-based and Git-native
Multi-agent orchestration should be represented in files and versioned in Git from day one. Task files with explicit status metadata make workflow state observable, auditable, and automation-friendly. Git worktrees then provide safe parallel isolation for agent edits, with controlled merges as a separate step.
