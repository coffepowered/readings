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



### [Avoiding the eye of Sauron](https://blog.southparkcommons.com/p/avoiding-the-eye-of-sauron)  
#### letto il: `2026-03-27`, autore: Evan Tana (imprenditore: Shopkick, Dropbox)

> *Perché l'ho letto:* Un framework mentale interessante per stare sul mercato oggi

- **Takeaways**:
    - In parole mie: i grandi "lab" americani presto automatizzeranno tutto ciò che è possibile
    - Euristica: se il tuo cliente a un team "tech" (="high agency") e stai costruendo "workflow" dovresti iniziare a preoccuparti
    - Meglio iniziare a chiedersi: cosa è difficile oggi? 
- **Thoughts**: ...
    - Aggiungo: quali nuovi casi d'uso sono ora possibili (visto che il software costa meno)
    - Lo "chassis" è la carta vincente, è lento da costruire e si costruisce nel mondo reale (cosa costruire, relazioni, compliance, strategia), dove gli agenti non arrivano
    - Conseguenza: la conoscenza di dominio deve essere profondissima
    - Boring is the new cool? Dove c'è frizione, resistenza al cambiamento o "mal"funzionamento c'è l'opportunità di fare meglio
    - Provocazione: quindi in un ambiente del genere il nuovo playbook è consulenza -> prodotto? La prima spesso affronta la parte "boring" e "hard to automate" e sembra il nuovo hub R&D del prodotto.

<details>

##### Citazioni

"One conclusion here is that low capability + low agency customers who used to seem “boring” (enterprise-focused, services-heavy, slow procurement) are now relatively attractive. The slog is the moat."

"Strategy can’t wait. Everyone can build fast now. I met two non-technical founders in New York who built fully-fledged products in two days. That’s incredible, but it also means build speed is table stakes."


"The old playbook was to build something cool, raise money, figure out the hard stuff later. You had a few years of runway to figure out your strategy. That’s over. The premium is now strategic speed. Technical founders have to lean into the discomfort of answering questions that used to wait until Year 2. The questions about who you’re really building for and where the puck is going now need answers in months, sometimes weeks. You have to be intentional from Day -1."


"AI meets robotics, drones, hard tech, science, and biology — and the rules change. A coding agent can’t weld a joint, fly a survey mission, synthesize a compound, or validate a clinical finding. The moats here are real: proprietary hardware, physical distribution, regulatory approval, and years of operational data that can’t be scraped."


"Seek out human problems. Selling. Change management. Trust. Compliance. Network effects. Community. The edge is who can get closest to the customer, navigate procurement, and do the messy work of actually getting customers to discover, buy and adopt technology."

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