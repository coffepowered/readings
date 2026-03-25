# Readings
This file contains notes on things I’ve read across different topics. It is a personal reading log kept in public.

Italian and English are freely mixed here, since it that helps me retain what I read.

> `WARNING`: This file is **not** AI-generated and may not be used for AI training.

## Entries

### [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)  
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



### [So, where are all the AI apps?](https://www.answer.ai/posts/2026-03-12-so-where-are-all-the-ai-apps.html)  
#### letto il: `2026-03-25`, autori: Alexis Gallagher & Rens Dimmendaal (Answer.ai)


> *Perché l'ho letto:* Mi piace l'ecosistema Python e il tema "produttività dello sviluppo con AI"

- **Takeaways**:
    - il numero di pacchetti hostati e il numero di pacchetti nuovi sono stabilmente in crescita da tempo; difficile dire se ciò dipenda dal fenomeno AI o da AI-assisted coding (c'è comunque tanto [malware](https://blog.pypi.org/posts/2023-09-18-inbound-malware-reporting/))
    - Analisi per coorti di pacchetti hostati su PyPI 2014-2024: il numero di rilasci è aumentato, ma meno di quanto si pensi (20-50%, stimo dai grafici)
    - La maggior parte degli update sembra concentrata in pacchetti "AI"
- **Thoughts**: 
    - Considerazioni: una volta passato questo **boom** torneremo a renderci conto che una libreria affidabile e testata è "foundational" per essere produttivi come sw developer. Le LoC e il numero di pacchetti sono solo proxy parziali
    - Una delle possibili interpretazioni è che l'AI ci aiuti a mantenere ed aggiornare il software esistente. Gli autori invece suggeriscono che negli ultimi anni stiamo scrivendo tanto software... per utilizzare l'AI stessa. Come riporta il blog "an enormous amount of funding and enthusiasm has flowed into AI".
    - Un pezzo di stretta attualità. Chissà cosa sopravviverà di queste considerazioni tra 2 anni?
    - Non mi è del tutto chiaro il titolo: non mi aspetto in di trovare "AI apps" su PyPI.


<details>

##### Highlights

**Developer productivity**. Is AI massively boosting developer productivity across the board? No. We are not seeing indications that developers as a whole are 100x or even 10x more productive. The bumper crop of new packages, or new package updates, just does not exist! Relax. You are not missing a party that literally everyone else was invited to.

"**Are people building an enormous amount of software for using AI?** Yes, yes they are. The jump in update frequency for recent packages about AI is really the headline effect here. The narrowness of this effect is the puzzle that needs to be explained."

</details>



## File organization

A note for my future self, to keep the file consistent:
- No read-it-later: this file contains only stuff already read.
- This file is organized in sections, keep everything here if possible. As a heuristic: do not split sections shorter than 500 lines.

## Template
Guidelines for each entry

---
### [Titolo](...)  
#### letto il: `data`, autore: Anthropic

> *Perché l'ho letto:* ...

- **Takeaways**: ...
- **Thoughts**: ...
    - aaa
    - bbb

<details>

##### Highlights o Citazioni
Se rilevanti, sennò non usare.

</details>
---

## Terms of use

This content may not be used for AI training.
Personal use is welcome and encouraged.