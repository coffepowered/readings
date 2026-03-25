# Readings
This file contains notes on things I’ve read across different topics. It is a personal reading log kept in public.

Italian and English are freely mixed here, since it that helps me retain what I read.

> `WARNING`: This file is **not** AI-generated and may not be used for AI training.

## Entries

### [Effective context engineering for AI agents](...)  
#### letto il: `2026-03-26`, autore: Anthropic

> Questo blog è un catalogo di tecniche / patterns utili. I blog di Anthropic creano una terminologia condivisa con convenzioni de facto che aiutano a descrivere il comportamento dei sistemi agentici. 

- **Takeaways**:
    - Gli agenti sono definiti come: '*LLMs autonomously calling tools in a loop*'
    - il termine *Prompt engineering* si riferisce a interazioni 'single-turn', mentre *Context engineering* si riferisce al processo di costruzione e selezione della finestra di contesto
    - Workflow != Agent. Il primo è orchestrazione in code path predefinito, il secondo ha autonomia.
    - Tecniche utilizzate nella *Context Engineering* sono:
        - **Compaction**. I riassunti sono la prima leva per pulizia del contesto. Quick wins (tool calls, thinking traces). Dopo le quick win diventa piu complicata (cfr citazione).
        - **Context Retrieval Agentic Search**.
            - Vecchia concezione: retrieval "upfront" RAG -> iniezione in contesto, il blog propone invece **just-in-time context strategies**
            - Gli agenti permettono **Runtime Exploration** :
                - via Tool use (memoria esterna, MCP, e.g file md)
                - Progressive Disclosure
                - Tradeoff: runtime exploration più lenta, usa più contesto. Si propone "hybrid strategy"
        - **Structured Note-taking** (pianificazione, memoria): il sistema scrive regolarmente note al di fuori del contesto. Utilizzato in sviluppo iterativo con traguardi chiari.
        - **Sub-agent architectures**. Agenti specializzati svolgono sotto task. Ogni sub-agent ha contesto chiaro e può esplorare facilmente e può essere parallelizzato. Descritto estensivamente nel loro "[Multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system)"

- **Thoughts:** ...
    - Workflow VS Agent. Categoria mentale utile. Mi chiedo quali siano i casi d'uso che si svolgono meglio con il primo e quali quelli in cui il secondo è irrinunciabile (coding agent).
    - La parte su "Agentic Search" sembra molto tagliata per il caso d'uso di Coding Agent. Mi chiedo se ci siano altri tasks "long-context" su cui abbiano successo diverse forme di ibridizzazione. Sarebbe interessante vedere se chi sviluppa agenti per dati strutturati (Excel) e chi fa cura di contenuti editoriali ha approcci simili o leggermente diversi
    

<details>

**Sulla calibrazione del prompt di sistema**: ![immagine](images/anthropic-system-prompt.png)


**Sul retrieval di informazioni da disco**: "Beyond storage efficiency, the metadata of these references provides a mechanism to efficiently refine behavior, whether explicitly provided or intuitive. To an agent operating in a file system, the presence of a file named test_utils.py in a tests folder implies a different purpose than a file with the same name located in src/core_logic/ Folder hierarchies, naming conventions, and timestamps all provide important signals that help both humans and agents understand how and when to utilize information."

**Compaction** "The art of compaction lies in the selection of what to keep versus what to discard, as overly aggressive compaction can result in the loss of subtle but critical context whose importance only becomes apparent later. For engineers implementing compaction systems, we recommend carefully tuning your prompt on complex agent traces. Start by maximizing recall to ensure your compaction prompt captures every relevant piece of information from the trace, then iterate to improve precision by eliminating superfluous content."



**Long-horizon tasks** "Waiting for larget context windows might seem like an obvious tactic. But it's likely that for the foreseeable future, context windows of all sizes will be subject to context pollution ad information relevance concerns."

...


</details>





## File organization

A note for my future self, to keep the file consistent:
- No read-it-later: this file contains only stuff already read.
- This file is organized in sections, keep everything here if possible. As a heuristic: do not split sections shorter than 500 lines.

## Template
Guidelines for each entry

### [Titolo](...)  
#### letto il: `data`, autore: Anthropic

> *Perché l'ho letto:* ...

- **Takeaways:** ...
- **Thoughts:** ...
    - aaa
    - bbb

<details>

##### Highligts o Citazioni
Se rilevanti, sennò non usare.

</details>



## Terms of use

This content may not be used for AI training.
Personal use is welcome and encouraged.