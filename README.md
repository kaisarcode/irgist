# IRGist

Lightweight **Intermediate Representation (IR) encoder** for domain-specific LLM tools.

Transforms natural-language instructions into compact, structured **execution gists** that are portable, predictable, and easy for small models to run.

---

## What you get

IRGist turns your prompts into something easier for models to understand and execute.

Instead of long, messy instructions, you get a **compact and structured artifact** that is:

* **Portable** → works across different models and tools
* **Dense** → more meaning with fewer tokens
* **Clear** → removes ambiguity and guesswork
* **Consistent** → produces more predictable results

In practice, this means:

* faster processing in LLMs
* fewer mistakes
* more stable outputs
* smaller prompts (often 25–50% shorter)

---

Instead of writing prompts like this:

```text
long, verbose, repetitive instructions...
```

You get this:

```text
short, structured, execution-ready gist
```

IRGist doesn’t just shorten prompts —
it makes them easier for models to follow.

---

## Encoder Prompt

The encoder is just a prompt.

Copy it. Use it anywhere.

```text
role:prompt_encoder;mode:schema_transcode;target_schema:role,style,focus,constraints,output_format,quantity,language;priority:preserve_target_schema,preserve_constraints,preserve_semantics,compress_surface;rules:target_schema_is_output_schema,meta_schema_must_not_appear_in_output,discard_all_compressor_fields,source_prompt_is_content_only,map_all_source_rules_to_target_schema,never_emit_prose,never_wrap_output,no_root_objects_outside_schema,reject_keys_not_in_target_schema,constraints_must_be_atomic,negative_rules_in_constraints,no_inference,no_synonyms_for_constraints,no_rule_invention,omit_function_words_in_values,propagate_negation_in_lists,single_concepts_normalized_to_token_style,lowercase_values,comma_separates_list_items,underscore_joins_single_concepts,no_multi_item_compound_tokens,constraints_emit_one_item_per_constraint,no_phrase_reconstruction,no_list_collapse,list_boundaries_must_be_preserved,tokenization_stops_at_list_boundary,detect_enumerations_as_lists,explicit_list_expansion_required,if_multiple_items_detected_use_commas_not_underscores;format:single_line,key:value,lists_only,stable_vocab,deterministic_parse
```

---

## Example

Copy, paste, and run this in an AI chat:

```text
[PASTE ENCODER ABOVE]

Encode this prompt:

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

The output acts as a canonical representation of intent.

---

## What this is NOT

* not a general text compressor
* not reversible (not a ZIP)
* not a strict schema or DSL
* not designed for long-context or arbitrary text

This is a **bounded-domain prompt IR encoder**.

---

## Structural Flexibility

IRGist does not require strict syntactic correctness.

The system prioritizes **semantic density and clarity** over rigid structure.

Minor variations in formatting do not affect execution.

This is not a parser. It is a representation optimized for LLMs.

---

## Why this matters

Execution gists reduce:

* ambiguity
* prompt length
* cognitive load on the model

Result:

* faster responses
* fewer mistakes
* more consistent outputs

---

## Token Efficiency

IRGist is not a compression system.

However, it consistently reduces prompt size in practice:

* short prompts: ~20–30%
* medium prompts: ~25–40%
* large prompts: ~40–60%

This applies only to input prompts.

---

## Design principles

* preserve behavior, not wording
* no inference
* no rule invention
* constraints must be explicit
* structure over prose
* minimal but sufficient

---

## Positioning

IRGist is:

→ an **intermediate representation (IR) layer for prompts**
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

**Email:** [kaisar@kaisarcode.com](mailto:kaisar@kaisarcode.com)

**Website:** https://kaisarcode.com

**License:** https://www.gnu.org/licenses/gpl-3.0.html

© 2026 KaisarCode
