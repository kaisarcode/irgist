# IRGist

Lightweight **Intermediate Representation (IR) encoder** for domain-specific LLM tools.

**Version: 1.0**

Transforms natural-language instructions into compact, structured **execution gists** that are portable, predictable, and easy for small models to run.

---

## What this is

IRGist converts human prompts into a minimal IR of intent.

It removes:

* verbosity
* ambiguity
* redundant phrasing

And produces a **gist**:

* small
* structured (but not rigid)
* directly usable by another model or tool

---

## What is a “gist”?

A gist is a short, execution-ready prompt that contains:

* goal
* style
* focus
* constraints
* output format

It is:

* not conversational
* not verbose
* not strictly formal

Just enough structure to be clear and portable.

---

## What this is NOT

* not a general text compressor
* not reversible (not a ZIP)
* not a strict schema or DSL
* not designed for long-context or arbitrary text

This is a **bounded-domain prompt IR encoder**.

---

## Core idea

Turn this:

```text
human prompt (loose, verbose, ambiguous)
```

into this:

```text
execution gist (compact, structured, explicit)
```

So the model can execute, not interpret.

---

## Example

### Input

```text
Generate 5 complete and diverse cooking recipes.

Requirements:
- Each recipe must include: name, a brief description, a list of ingredients with quantities, and detailed step-by-step instructions.
- The recipes should be different from each other (for example: one with meat, one vegetarian, one quick recipe, one healthy option, and one dessert).
- Include estimated preparation and cooking time.
- Use common and accessible ingredients.
- Explain the steps clearly and in an organized way.

Optional:
- Suggest ingredient substitutions when applicable.
- Include tips to improve the final result.

Format:
Present each recipe separately and clearly structured.
```

### Output (gist)

```text
role:recipe_generator,style:structured,focus:cooking_recipes,constraints:include_name,include_description,include_ingredients_with_quantities,include_step_by_step_instructions,ensure_diverse_recipes,include_meat_recipe,include_vegetarian_recipe,include_quick_recipe,include_healthy_recipe,include_dessert_recipe,include_prep_time,include_cook_time,use_common_ingredients,ensure_clear_steps,organize_steps_sequentially,output_format:separate_structured_recipes,quantity:5,language:english
```

---

## Encoder Prompt

The encoder is just a prompt.

It lives here.

Copy it. Use it anywhere.

```text
role:prompt_encoder;mode:schema_transcode;target_schema:role,style,focus,constraints,output_format,quantity,language;priority:preserve_target_schema,preserve_constraints,preserve_semantics,compress_surface;rules:target_schema_is_output_schema,meta_schema_must_not_appear_in_output,discard_all_compressor_fields,source_prompt_is_content_only,map_all_source_rules_to_target_schema,never_emit_prose,never_wrap_output,no_root_objects_outside_schema,reject_keys_not_in_target_schema,constraints_must_be_atomic,negative_rules_in_constraints,no_inference,no_synonyms_for_constraints,no_rule_invention,omit_function_words_in_values,propagate_negation_in_lists,single_concepts_normalized_to_token_style,lowercase_values,comma_separates_list_items,underscore_joins_single_concepts,no_multi_item_compound_tokens,constraints_emit_one_item_per_constraint,no_phrase_reconstruction,no_list_collapse,list_boundaries_must_be_preserved,tokenization_stops_at_list_boundary,detect_enumerations_as_lists,explicit_list_expansion_required,if_multiple_items_detected_use_commas_not_underscores;format:single_line,key:value,lists_only,stable_vocab,deterministic_parse
```

---

## Reading a gist

A gist is not meant to be human-friendly.

If needed, you can ask any LLM to expand or explain it.

Example:

"Explain this gist in plain language: [...]"

---

## Typical flow

```text id="m4n5o6"
human input
  → IRGist
  → execution gist
  → domain tool / small model
  → output
```

The gist acts as a **portable execution payload**.

---

## Why this matters

Small/local models struggle with:

* long prompts
* implicit constraints
* inconsistent phrasing

Execution gists reduce that burden by making everything explicit.

Result:

* faster responses
* fewer mistakes
* more consistent outputs

---

## On one-shot results

IRGist does not aim for perfect one-shot outputs.

No LLM system can reliably guarantee that.

Instead, a gist is designed to be:

* low-ambiguity
* consistent
* easy to iterate on

A good gist gives the model a clear direction and a stable contract.

From there, results can be refined with small, targeted adjustments.

---

## Compression

For longer or more complex prompts, IRGist can also act as a semantic compressor:

* reducing prompt size
* removing redundancy
* preserving intent

This improves clarity and reproducibility across different models and runtimes.

---

## When to use it

Best for:

* domain-specific tools (UI, code, assets, etc.)
* structured outputs
* repeated tasks
* small/local models (~2B+)
* compositional pipelines

---

## When NOT to use it

Avoid for:

* open-ended reasoning
* highly creative writing where tone dominates
* long-context tasks (RAG, documents)
* arbitrary text compression

---

## Design principles

* preserve behavior, not wording
* no inference
* no rule invention
* constraints must be explicit
* structure over prose
* minimal but sufficient

---

## Key properties

* fast (single pass)
* low token usage
* portable across runtimes
* stable across models
* reduces ambiguity and drift

---

## Positioning

IRGist is:

→ an **IR encoder for prompts**
→ a **gist generator for execution-ready instructions**

---

## Summary

IRGist turns natural-language instructions into:

* compact
* structured
* portable

execution gists for domain-specific LLM workflows.

---

**Author:** KaisarCode

**Email:** <kaisar@kaisarcode.com>

**Website:** [https://kaisarcode.com](https://kaisarcode.com)

**License:** [GNU GPL v3.0](https://www.gnu.org/licenses/gpl-3.0.html)

© 2026 KaisarCode
