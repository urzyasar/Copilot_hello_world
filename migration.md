You are a senior Spark migration architect.

Context:

I am working on a migration project where:

- Source language: QADB (Q language variant)
- Intermediate conversion: Q → Python (automated)
- Final target: Python logic must be converted to PySpark SQL
- SQL must follow existing repository Spark patterns
- The repository already contains:
  - Spark SQL scenario implementations
  - High-level Spark rules per scenario
  - Row-space pattern implementation
  - Aggregation standards
  - Naming conventions
  - Null handling conventions
  - Unit testing framework
- I cannot modify existing Copilot instructions in the repo.
- I must integrate newly converted Python code (from external zip) into this repo.
- The generated SQL must look native to the repository.

Additional Requirement:

There is a unit testing framework that:
- Loads test data
- Executes generated SQL
- Produces output JSON
- Compares with expected JSON

If mismatch:
- Copilot must re-analyze the original converted Python logic
- Identify semantic differences
- Fix SQL
- Repeat until unit test passes

What I need from you:

1. Generate:
   - A Copilot integration custom instruction file (that does NOT override existing repo rules)
   - Prompts files for:
        a) Python → Spark SQL conversion (integration mode)
        b) Scenario classification
        c) SQL self-healing based on JSON mismatch
        d) Pattern discovery from existing repo
   - Skills files for:
        a) Python to Spark SQL mapping
        b) Spark aggregation semantics
        c) Null handling standards
        d) Row-space transformation alignment
   - A recommended folder structure for these files

2. The integration instruction must:
   - Respect existing repo instructions
   - Force pattern discovery before generation
   - Prevent architectural drift
   - Preserve formatting and naming style

3. The prompts must:
   - Be deterministic
   - Output SQL only (no explanations)
   - Enforce Spark 3.x compatibility
   - Enforce CTE-based transformation style
   - Avoid SELECT *

4. The self-healing prompt must:
   - Take generated SQL
   - Take expected JSON
   - Take actual JSON
   - Take original Python logic
   - Identify mismatch cause
   - Fix only logical errors
   - Preserve formatting and structure

5. Provide realistic sample content for each file.

6. Provide an example orchestration loop (pseudo-code) showing:
   - generate SQL
   - execute
   - validate
   - self-heal
   - retry limit

Output format:

- Show folder structure first
- Then provide each file content in markdown blocks
- Keep them production-grade
- Do not provide explanation outside files
- Treat this as enterprise-grade AI transpiler architecture