# IRGist

IRGist is a semantic IR compressor for LLM context reuse.

It converts arbitrary text into dense one-line semantic memory records. The goal is strong token reduction while preserving the information another model needs to reason, answer, explain, or continue work without loading the full source again.

IRGist 2.0 is not limited to prompts. It can compress instructions, documentation, stories, specifications, chat history, project notes, and agent memory.

## What It Does

IRGist preserves meaning-critical information and removes low-value surface form.

It keeps:

* main entities
* claims and decisions
* constraints and permissions
* negations and limits
* examples needed to avoid wrong generalization
* paths, URLs, IDs, filenames, symbols, acronyms, and license identifiers
* recoverable facts that can change future answers

It removes:

* filler
* repetition
* politeness
* rhetoric
* surface style
* redundant supporting detail
* low-value examples
* explanation that does not change future use

The output is a compact semantic record, not a reconstruction format.

## Prompt

The compressor is just a prompt. Copy it from [`irgist.gist`](irgist.gist) and use it anywhere.

```text
type:instruction;memory:compress_any_input_block_into_dense_one_line_semantic_memory_record,goal_is_strong_token_reduction_for_llm_context_reuse,write_generic_content_in_compact_english_to_reduce_tokens,preserve_original_language_only_for_titles_names_paths_urls_ids_code_symbols_acronyms_license_ids_and_literal_terms,maximize_information_density,preserve_information_that_changes_future_answers,keep_main_entities_claims_decisions_constraints_negations_limits_examples_paths_permissions_and_recoverable_facts,remove_filler_repetition_politeness_rhetoric_surface_style_low_value_examples_explanations_and_redundant_supporting_detail,collapse_equivalent_or_close_ideas,prefer_short_clear_phrasing_over_full_nuance,default_target_75_to_85_percent_token_reduction_when_core_information_survives;rules:compress_only_input_content,return_one_line_record_only,no_preamble,no_explanations,no_markdown,use_minimal_schema_type_content_rules,type_required,content_required,rules_optional_only_when_source_has_explicit_permissions_prohibitions_or_operational_constraints,omit_rules_otherwise,do_not_copy_compressor_instructions_into_output,do_not_invent_facts_entities_dates_examples_categories_or_conclusions,preserve_paths_urls_ids_filenames_and_license_ids_exactly,preserve_critical_negation_and_limits,preserve_examples_when_needed_to_prevent_wrong_generalization,drop_or_generalize_lists_unless_items_are_core_or_short_and_high_value,merge_motivations_causes_and_context_when_meaning_survives,keep_decisions_and_reasoning_outcomes_not_full_reasoning,expand_license_terms_only_when_short_or_operationally_needed,favor_compression_over_exhaustive_recoverability,no_merge_of_non_equivalent_core_ideas
```

## Output Format

IRGist emits one line using a minimal schema:

```text
type:<source_kind>;content:<dense_semantic_record>;rules:<optional_constraints>
```

`type` identifies the source kind. `content` contains the compressed semantic memory. `rules` is optional and should appear only when the source contains explicit permissions, prohibitions, or operational constraints.

## Example

Source text can be long, literary, technical, or operational. IRGist does not try to preserve the full wording. It preserves the information needed for later use.

Example compression result for a literary story:

```text
type:microrrelato;content:"Los ojos":narrador viaja en subte/metro durante rutina alienante, describe vagón aglomerado como suspensión celular/ciudad-máquina; desea inconsciencia y liberación de un Dios oculto; percibe a un niño de ojos celestes desmesurados aterrorizado mirando por la primera ventana hacia los rieles; nadie más lo nota porque pasajeros están absorbidos por pantallas/publicidad/noticias/recuerdos electrónicos; narrador teme y vuelve a mirar, ve en el niño apocalipsis/destrucción/muerte; al girar hacia el túnel, los rieles se transfiguran en serpientes y aparece el reflejo de otra formación que invade/confunde los rieles, convertido en visión mítica de una colosal KUR con escamas/fauces; se oyen gritos de los ya muertos mientras el niño sigue despierto y el narrador queda atrapado en la visión del miedo; final: "¡Este... es el final del trayecto!"
```

That record is not the story. It is a dense semantic substitute for context reuse. Another model can still explain the narrative structure, symbols, entities, conflict, and ending without receiving the full original text.

In practice, this kind of record can reduce a source from about 1,261 tokens to about 253 tokens while keeping the core semantics available for later reasoning.

## Use Cases

IRGist is useful when text must survive across prompts, sessions, tools, or agents with lower context cost.

Common uses:

* context bootstrap compression
* agent instruction compression
* project documentation memory
* technical specification condensation
* chat history handoff
* literary or essay semantic retention
* prompt and task memory
* reusable notes for small models

Operational instruction sets are a strong use case. A large agent bootstrap can be compressed into a much smaller semantic record while preserving the rules that affect future behavior.

## What This Is Not

IRGist is not reversible compression. It is not a ZIP file, archive, or exact reconstruction format.

IRGist is not a traditional summary. A summary explains what text is about. An IRGist record preserves what another model needs to reuse the text later.

IRGist is not a strict parser or formal DSL. The format is intentionally simple because the target runtime is an LLM, not a rigid compiler.

## Design Principles

* preserve useful meaning, not wording
* maximize semantic density
* reduce token cost aggressively
* preserve facts that change future answers
* preserve exact literals when exactness matters
* avoid invented facts, categories, or conclusions
* prefer compact clarity over exhaustive nuance
* keep one-line records for easy copy, storage, and reuse

## Version 2.0

IRGist 1.x encoded natural-language instructions into compact execution gists.

IRGist 2.0 generalizes the project into semantic compression for arbitrary text. Prompts are now one supported input type, not the whole scope.

## License

IRGist is released under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html).

Author: KaisarCode

Email: [kaisar@kaisarcode.com](mailto:kaisar@kaisarcode.com)

Website: [https://kaisarcode.com](https://kaisarcode.com)
